# Pytest -- Python Testing Notes

> Practical notes based on the supplied Pytest tutorial transcript.
> Organized for revision and backend engineering practice.

## 1. Introduction to Testing

### What is software testing?

Software testing verifies whether code behaves as expected. It helps: -
Find bugs before production. - Prevent changes from breaking existing
functionality. - Improve reliability and maintainability.

### What is Pytest?

Pytest is a Python testing framework used to write and execute automated
tests.

**Why use Pytest?** - Automatically discovers tests. - Uses simple
Python `assert` statements. - Produces readable failure reports. -
Supports reusable fixtures. - Supports parameterized tests and
markers. - Works with mocking tools and plugins.

## 2. Installation and Project Setup

Install Pytest:

``` bash
pip install pytest
pytest --version
```

Example project structure:

``` text
my_project/
├── source/
│   ├── __init__.py
│   ├── my_functions.py
│   └── service.py
└── tests/
    ├── test_my_functions.py
    ├── test_service.py
    └── conftest.py
```

### Naming conventions

  Component       Convention
  --------------- ----------------------------
  Test file       `test_*.py` or `*_test.py`
  Test function   `test_*()`
  Test class      `Test*`
  Test method     `test_*()`

Pytest discovers tests automatically when they follow its naming
conventions.

### Running tests

``` bash
pytest                                  # Run discovered tests
pytest -v                               # Verbose output
pytest -s                               # Show print statements
pytest -q                               # Quiet output
pytest tests/                           # Run a directory
pytest tests/test_service.py            # Run one file
pytest tests/test_service.py::test_get  # Run one test
pytest -k add                           # Run tests matching expression
pytest -m slow                          # Run tests with a marker
pytest --tb=short                       # Short traceback
pytest -x                               # Stop after first failure
pytest --maxfail=2                      # Stop after two failures
```

## 3. Basic Testing with Assertions

`assert` checks whether a condition is true: - If true, the test
passes. - If false, Pytest reports an assertion failure.

Application code:

``` python
def add(a, b):
    return a + b
```

Test:

``` python
def test_add():
    result = add(1, 4)
    assert result == 5
```

Test different inputs and data types:

``` python
def test_add_strings():
    assert add("I like ", "burgers") == "I like burgers"
```

Example test cases:

  Input                      Expected output
  -------------------------- -----------------
  `add(2, 3)`                `5`
  `add(-2, 3)`               `1`
  `add(0, 0)`                `0`
  `add("Hello ", "World")`   `"Hello World"`

Test normal inputs, boundary inputs and invalid inputs. A test
containing only `pass` may pass, but it does not verify application
behavior.

## 4. Testing Exceptions

Use `pytest.raises()` when an exception is the expected behavior.

``` python
import pytest

def divide(a, b):
    return a / b

def test_divide_by_zero():
    with pytest.raises(ZeroDivisionError):
        divide(10, 0)
```

Custom exception example:

``` python
def divide(a, b):
    if b == 0:
        raise ValueError("Cannot divide by zero")
    return a / b

def test_divide_by_zero():
    with pytest.raises(ValueError):
        divide(10, 0)
```

**Remember:** The test passes when the expected exception is raised. It
fails if no exception or a different exception is raised.

## 5. Testing Classes

Tests can be grouped inside classes. This is useful when testing class
methods.

Example application:

``` python
import math

class Shape:
    def area(self):
        pass

    def perimeter(self):
        pass

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return math.pi * self.radius ** 2

    def perimeter(self):
        return 2 * math.pi * self.radius
```

Class-based tests:

``` python
import math

class TestCircle:
    def setup_method(self):
        self.circle = Circle(10)

    def test_area(self):
        assert self.circle.area() == math.pi * 10 ** 2

    def test_perimeter(self):
        assert self.circle.perimeter() == 2 * math.pi * 10
```

### Setup and teardown

  Method                When it runs              Purpose
  --------------------- ------------------------- -------------------------
  `setup_method()`      Before each test method   Initialize test objects
  `teardown_method()`   After each test method    Clean up resources

Execution order:

``` text
setup_method()
    ↓
test_one()
    ↓
teardown_method()
    ↓
setup_method()
    ↓
test_two()
    ↓
teardown_method()
```

Run `pytest -s` to display print statements.

## 6. Fixtures

### What is a fixture?

A fixture is a reusable function that supplies data, objects or
resources required by tests.

Without a fixture, tests may repeatedly create the same object:

``` python
def test_area():
    rectangle = Rectangle(10, 20)
    assert rectangle.area() == 200

def test_perimeter():
    rectangle = Rectangle(10, 20)
    assert rectangle.perimeter() == 60
```

With a fixture:

``` python
import pytest

@pytest.fixture
def my_rectangle():
    return Rectangle(10, 20)

def test_area(my_rectangle):
    assert my_rectangle.area() == 200

def test_perimeter(my_rectangle):
    assert my_rectangle.perimeter() == 60
```

Pytest identifies the fixture by its function name and injects its
return value into the test.

### Fixture scopes

  Scope        Lifetime
  ------------ ---------------------------------
  `function`   Once per test function; default
  `class`      Once per test class
  `module`     Once per test module
  `package`    Once per package
  `session`    Once per test session

Example:

``` python
@pytest.fixture(scope="module")
def database():
    return create_database()
```

A broader scope can reduce repeated setup, but shared state can make
tests interfere with each other. Choose the narrowest scope that meets
the need.

### Fixture teardown with `yield`

``` python
@pytest.fixture
def database():
    db = connect_database()
    yield db
    db.close()
```

Execution: 1. Connect to the database. 2. Yield the connection to the
test. 3. Run the test. 4. Close the connection after the test finishes.

### Autouse fixtures

An autouse fixture runs automatically without being named as a test
argument.

``` python
@pytest.fixture(autouse=True)
def setup():
    print("Running before every test")
```

Use autouse sparingly because it can hide setup dependencies.

### `conftest.py`

`conftest.py` stores fixtures that can be shared by test files in its
directory tree.

Example:

``` text
tests/
├── conftest.py
├── test_circle.py
├── test_rectangle.py
└── test_square.py
```

``` python
# tests/conftest.py
import pytest

@pytest.fixture
def my_rectangle():
    return Rectangle(10, 20)
```

Tests in the relevant directory and its subdirectories can use this
fixture without importing it.

Common fixture use cases: - Database connections. - API clients. -
Authentication tokens. - Reusable test data. - Common test objects.

Keep fixtures local when they are only needed by one test module.

## 7. Markers

Markers attach metadata to tests and help control test execution.

### Skip

Skip a test unconditionally:

``` python
@pytest.mark.skip(reason="Feature is broken")
def test_add():
    assert add(1, 2) == 3
```

### Skip if

Skip based on a condition:

``` python
import sys

@pytest.mark.skipif(
    sys.platform == "win32",
    reason="Not supported on Windows"
)
def test_feature():
    assert True
```

### Xfail

Mark a test that is expected to fail:

``` python
@pytest.mark.xfail(reason="Known bug")
def test_divide():
    assert divide(10, 0) == 5
```

An expected failure is reported as `XFAIL`. If it unexpectedly passes,
Pytest can report `XPASS`.

### Custom markers

``` python
@pytest.mark.slow
def test_large_calculation():
    assert sum(range(100000)) > 0
```

Run only tests with the marker:

``` bash
pytest -m slow
```

Register custom markers in `pytest.ini`:

``` ini
[pytest]
markers =
    slow: marks tests as slow
    integration: integration tests
    unit: unit tests
```

## 8. Parameterized Testing

### What is parameterization?

Parameterization runs the same test function with multiple sets of input
values. It avoids writing separate test functions for each case.

``` python
import pytest

@pytest.mark.parametrize(
    "input_value, expected",
    [
        (5, 25),
        (4, 16),
        (9, 81),
    ]
)
def test_square(input_value, expected):
    assert input_value ** 2 == expected
```

Each parameter set becomes an independently reported test case.

Multiple parameters:

``` python
@pytest.mark.parametrize(
    "a, b, expected",
    [
        (2, 3, 5),
        (5, 5, 10),
        (-2, 2, 0),
        (0, 0, 0),
    ]
)
def test_add(a, b, expected):
    assert add(a, b) == expected
```

### Parameterization vs loops

  -----------------------------------------------------------------------
  Loop inside a test                  Parameterization
  ----------------------------------- -----------------------------------
  Multiple cases run inside one test  Each case is a separate test case

  Failures can be harder to isolate   Failed input is identified clearly

  Less detailed test reporting        Better reporting and selection
  -----------------------------------------------------------------------

Use parameterization when testing the same behavior with different
inputs, boundary values or edge cases.

## 9. Mocking

### What is mocking?

Mocking replaces a dependency with a controlled fake object or function
during a test.

Why mock external dependencies? - Avoid slow network calls. - Avoid API
downtime and rate limits. - Avoid unpredictable external responses. -
Avoid unnecessary API costs. - Test application logic in isolation.

Common dependencies to mock: - External APIs. - Email services. -
Payment gateways. - Third-party services. - Other components whose
behavior is outside the unit under test.

### Python mock library

`unittest.mock` is included in Python's standard library:

``` python
from unittest.mock import Mock, patch
```

### Patching a function

``` python
from unittest.mock import patch

@patch("source.service.get_user_from_db")
def test_get_user(mock_get_user):
    mock_get_user.return_value = "Mocked Alice"

    username = service.get_user_from_db(1)

    assert username == "Mocked Alice"
```

`patch()` temporarily replaces the target with a mock during the test.

### Important mock properties and methods

``` python
mock_function.return_value = "Hello"
mock_function.assert_called_once()
mock_function.assert_called_once_with(1)
```

-   `return_value`: Controls what the mock returns when called.
-   `assert_called_once()`: Checks that it was called exactly once.
-   `assert_called_once_with(...)`: Checks that it was called exactly
    once with the specified arguments.

### Mocking an API request

Application code:

``` python
import requests

def get_users():
    response = requests.get(
        "https://jsonplaceholder.typicode.com/users"
    )

    if response.status_code == 200:
        return response.json()

    raise requests.HTTPError()
```

Test a successful response:

``` python
from unittest.mock import Mock, patch

@patch("source.service.requests.get")
def test_get_users(mock_get):
    mock_response = Mock()
    mock_response.status_code = 200
    mock_response.json.return_value = {
        "id": 1,
        "name": "John"
    }

    mock_get.return_value = mock_response

    data = service.get_users()

    assert data == {"id": 1, "name": "John"}
```

### Mocking an API error

``` python
import pytest
import requests
from unittest.mock import Mock, patch

@patch("source.service.requests.get")
def test_get_users_error(mock_get):
    mock_response = Mock()
    mock_response.status_code = 400
    mock_get.return_value = mock_response

    with pytest.raises(requests.HTTPError):
        service.get_users()
```

### How the mock works

1.  The test calls `get_users()`.
2.  `requests.get()` has been patched.
3.  The patched function returns the mock response.
4.  The application reads the mocked status code and JSON.
5.  The test checks the expected result or exception.

**Important:** Patch the name where the code under test looks it up. If
`service.py` uses `requests.get`, the target is generally
`source.service.requests.get`, not necessarily `requests.get`.

**Rule of thumb:** Mock external dependencies when their behavior is
outside the unit being tested. Test your own business logic rather than
testing the external service itself.

## 10. Using AI to Generate Tests

The tutorial demonstrates asking ChatGPT to generate Pytest tests for a
classroom application.

The example application contains: - `Classroom` - `Person` - `Teacher` -
`Student` - `TooManyStudents` custom exception

Classroom methods: - `add_student()` - `remove_student()` -
`change_teacher()` - `__init__()`

The classroom has a maximum capacity of 10 students. Adding a student
beyond the limit should raise `TooManyStudents`.

### Tests requested from AI

-   Fixtures for classroom and students.
-   Classroom creation test.
-   Add student test.
-   Maximum student limit test.
-   Remove student test.
-   Change teacher test.
-   Exception testing with `pytest.raises()`.
-   Parameterized tests.
-   Markers where appropriate.

### Important lesson: Validate AI-generated tests

The tutorial reveals a boundary-condition bug in the student limit
logic.

Incorrect:

``` python
if len(self.students) <= 10:
    self.students.append(student)
```

This allows another student when there are already 10 students.

Correct:

``` python
if len(self.students) < 10:
    self.students.append(student)
else:
    raise TooManyStudents
```

AI-generated tests are not automatically correct. Check: - Whether tests
reflect the actual requirements. - Whether boundary conditions are
correct. - Whether the expected behavior is correct. - Whether the tests
pass for the right reason.

Do not change correct application behavior merely to make an incorrect
test pass.

## 11. Useful Pytest Output Symbols

  Symbol   Meaning
  -------- --------------------------------------
  `.`      Passed
  `F`      Failed
  `E`      Error during test execution or setup
  `s`      Skipped
  `x`      Expected failure
  `X`      Unexpected pass

## 12. Important Differences

### Fixtures vs setup/teardown methods

  Fixture                      `setup_method()` / `teardown_method()`
  ---------------------------- ----------------------------------------
  Pytest-native mechanism      xUnit-style class methods
  Can be shared across tests   Associated with a test class
  Supports scopes              Runs around each test method
  Can inject dependencies      Commonly uses class instance state
  Supports `yield` cleanup     Uses a separate teardown method

### Fixture vs mock

  -----------------------------------------------------------------------
  Fixture                             Mock
  ----------------------------------- -----------------------------------
  Provides reusable resources or data Replaces a dependency

  Handles setup and teardown          Controls dependency behavior

  Can create a test client or test    Can simulate an API response
  object                              

  Reused across tests                 Used to isolate the code under test
  -----------------------------------------------------------------------

### Skip vs xfail

  Skip                              Xfail
  --------------------------------- -------------------------------
  Test is not executed              Test is executed
  Used when a test should not run   Used when failure is expected
  `pytest.mark.skip`                `pytest.mark.xfail`

### Unit vs integration testing

  -----------------------------------------------------------------------
  Unit testing                        Integration testing
  ----------------------------------- -----------------------------------
  Tests an individual component       Tests interactions between
                                      components

  Often mocks external dependencies   May connect real components

  Usually faster                      Usually slower

  Focuses on isolated logic           Focuses on component interactions
  -----------------------------------------------------------------------

## 13. Applying Pytest to Backend Engineering

For a backend containing FastAPI, PostgreSQL, Redis, Celery and external
APIs:

  Component                     Testing approach
  ----------------------------- -------------------------------
  Business logic                Assertions and unit tests
  API endpoints                 Pytest + FastAPI `TestClient`
  Database                      Fixtures and a test database
  Redis                         Fixtures or mocks
  External APIs                 Mocking
  Authentication                Fixtures
  Multiple input combinations   Parameterization
  Slow integration tests        Markers
  Resource cleanup              Fixture teardown

Example FastAPI endpoint:

``` python
from fastapi import FastAPI

app = FastAPI()

@app.get("/users/{user_id}")
def get_user(user_id: int):
    return {"user_id": user_id}
```

Test:

``` python
from fastapi.testclient import TestClient

client = TestClient(app)

def test_get_user():
    response = client.get("/users/10")

    assert response.status_code == 200
    assert response.json() == {"user_id": 10}
```

This tests the endpoint's HTTP response and returned JSON.

## 14. Best Practices

1.  Test important business logic.
2.  Cover normal, boundary and invalid inputs.
3.  Keep tests independent.
4.  Use descriptive test names.
5.  Avoid unnecessary mocking.
6.  Use fixtures for reusable setup.
7.  Use parameterization for multiple input combinations.
8.  Test exception handling.
9.  Mock external dependencies in unit tests.
10. Run tests before committing code.
11. Keep tests readable and maintainable.
12. Validate AI-generated tests.

## 15. Practical Exercises

Complete these in order:

1.  **Basic assertions:** Test addition, subtraction, multiplication and
    division.
2.  **Exception testing:** Test division by zero and invalid input
    handling.
3.  **Class-based testing:** Create a `BankAccount` class and test
    deposit and withdrawal.
4.  **Fixtures:** Create reusable database and user fixtures.
5.  **Fixture scopes:** Experiment with function, module and session
    scopes.
6.  **`conftest.py`:** Move shared fixtures into `conftest.py`.
7.  **Markers:** Create unit, integration and slow test markers.
8.  **Parameterization:** Test 10 different inputs using one test
    function.
9.  **Mocking:** Mock an external API and test successful and failed
    responses.
10. **FastAPI testing:** Test GET, POST, PUT and DELETE endpoints.
11. **Backend integration:** Test a FastAPI endpoint with a test
    database.

## 16. Final Revision Cheat Sheet

  Concept             Syntax
  ------------------- -----------------------------------
  Basic test          `def test_example():`
  Assertion           `assert actual == expected`
  Exception           `pytest.raises(ValueError)`
  Fixture             `@pytest.fixture`
  Fixture scope       `@pytest.fixture(scope="module")`
  Fixture cleanup     `yield`
  Automatic fixture   `@pytest.fixture(autouse=True)`
  Shared fixtures     `conftest.py`
  Skip                `@pytest.mark.skip`
  Conditional skip    `@pytest.mark.skipif`
  Expected failure    `@pytest.mark.xfail`
  Parameterization    `@pytest.mark.parametrize`
  Mocking             `@patch("module.function")`
  Mock return         `mock.return_value = value`
  Run tests           `pytest`

## Key Takeaway

The goal of testing as a backend engineer is to protect application
behavior against regressions, invalid inputs, external failures and
unexpected conditions.

Do not just memorize Pytest syntax. Practice writing tests for real
application code, especially API endpoints, database interactions,
business logic and external service integrations.
