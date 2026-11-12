


# Comprehensive Python Notes - W3Schools Tutorial
https://www.w3schools.com/python/

## **1. PYTHON INTRODUCTION**

### What is Python?
- Created by Guido van Rossum, released in 1991
- Popular programming language used for:
  - Web development (server-side)
  - Software development
  - Mathematics
  - System scripting
  - Big data handling
  - Rapid prototyping

### Why Python?
- Cross-platform (Windows, Mac, Linux, Raspberry Pi)
- Simple syntax similar to English
- Fewer lines of code compared to other languages
- Interpreter-based (quick execution)
- Supports procedural, object-oriented, and functional programming
- Uses indentation (whitespace) instead of curly brackets for scope definition

---

## **2. PYTHON SYNTAX**

### Execution Methods
- Command Line: `>>> print("Hello, World!")`
- File execution: `python myfile.py`

### Indentation
- **Critical** in Python (not just for readability)
- Indicates blocks of code
- Most common: 4 spaces (minimum 1 space)
- Must be consistent within the same block

```python
if 5 > 2:
    print("Five is greater than two!")
```

### Comments
- Start with `#`
- Single-line comments only

```python
# This is a comment
print("Hello, World!")
```

---

## **3. VARIABLES**

### Creating Variables
- No declaration command needed
- Created when first assigned a value
- Dynamic typing (can change type)

```python
x = 5          # int
y = "John"     # str
x = "Sally"    # x is now str
```

### Variable Naming Rules
- Case-sensitive (`a` ≠ `A`)
- Can use single or double quotes for strings
- Must start with letter or underscore
- Cannot start with number

### Casting
```python
x = str(3)     # "3"
y = int(3)     # 3
z = float(3)   # 3.0
```

### Getting Type
```python
type(x)  # Returns data type
```

### Multiple Assignment
```python
x, y, z = "Orange", "Banana", "Cherry"
a = b = c = "Apple"
```

### Global Variables
- Variables created outside functions
- Use `global` keyword to modify inside functions

---

## **4. DATA TYPES**

### Built-in Data Types

| Category | Types |
|----------|-------|
| Text | `str` |
| Numeric | `int`, `float`, `complex` |
| Sequence | `list`, `tuple`, `range` |
| Mapping | `dict` |
| Set | `set`, `frozenset` |
| Boolean | `bool` |
| Binary | `bytes`, `bytearray`, `memoryview` |
| None | `NoneType` |

### Setting Specific Types
```python
x = str("Hello")
x = int(20)
x = float(20.5)
x = list(("apple", "banana"))
x = dict(name="John", age=36)
```

---

## **5. NUMBERS**

### Three Numeric Types

**Int (Integer)**
- Whole numbers, positive/negative
- Unlimited length
```python
x = 1
y = 35656222554887711
z = -3255522
```

**Float**
- Numbers with decimals
- Scientific notation with 'e'
```python
x = 1.10
y = 35e3    # 35000.0
z = 12E4    # 120000.0
```

**Complex**
- Written with 'j' as imaginary part
```python
x = 3+5j
y = 5j
```

### Type Conversion
```python
a = float(x)      # int to float
b = int(y)        # float to int
c = complex(x)    # int to complex
# Note: Cannot convert complex to other types
```

### Random Numbers
```python
import random
print(random.randrange(1, 10))
```

---

## **6. CASTING**

Specify data type using constructor functions:
```python
x = int(1)       # 1
y = int(2.8)     # 2
z = int("3")     # 3
```

---

## **7. STRINGS**

### String Basics
- Surrounded by single or double quotes
- Multiline strings with triple quotes

### Slicing
```python
b = "Hello, World!"
print(b[2:5])    # "llo"
print(b[:5])     # "Hello"
print(b[2:])     # "llo, World!"
print(b[-5:-2])  # "orl"
```

### Modify Strings
```python
a = " Hello, World! "
print(a.upper())       # " HELLO, WORLD! "
print(a.lower())       # " hello, world! "
print(a.strip())       # "Hello, World!"
print(a.replace("H","J"))  # " Jello, World! "
print(a.split(","))    # [' Hello', ' World! ']
```

### Concatenation
```python
a = "Hello"
b = "World"
c = a + " " + b
```

### Format Strings
```python
age = 36
txt = f"My name is John, I am {age}"
price = 59
txt = f"The price is {price:.2f} dollars"
```

### Escape Characters
- `\'` Single quote
- `\"` Double quote
- `\\` Backslash
- `\n` New line
- `\t` Tab

### String Methods
- `capitalize()`, `casefold()`, `center()`, `count()`
- `encode()`, `endswith()`, `find()`, `format()`
- `index()`, `isalnum()`, `isalpha()`, `isdigit()`
- `join()`, `lower()`, `upper()`, `strip()`
- `replace()`, `split()`, `startswith()`, `swapcase()`

---

## **8. BOOLEANS**

```python
print(10 > 9)   # True
print(10 == 9)  # False
print(bool("")) # False
print(bool(0))  # False
```

Most values evaluate to `True` except:
- Empty values: `""`, `[]`, `{}`, `()`, `0`, `None`, `False`

---

## **9. OPERATORS**

### Arithmetic Operators
- `+` Addition
- `-` Subtraction
- `*` Multiplication
- `/` Division
- `%` Modulus
- `**` Exponentiation
- `//` Floor division

### Assignment Operators
- `=` Assign
- `+=` Add and assign
- `-=` Subtract and assign
- `*=` Multiply and assign
- `/=` Divide and assign

### Comparison Operators
- `==` Equal
- `!=` Not equal
- `>` Greater than
- `<` Less than
- `>=` Greater than or equal
- `<=` Less than or equal

### Logical Operators
- `and` - Returns True if both statements are true
- `or` - Returns True if one statement is true
- `not` - Reverse the result

### Identity Operators
- `is` - Returns True if both variables are the same object
- `is not` - Returns True if both variables are not the same object

### Membership Operators
- `in` - Returns True if sequence with specified value is present
- `not in` - Returns True if sequence with specified value is not present

### Bitwise Operators
- `&` AND
- `|` OR
- `^` XOR
- `~` NOT
- `<<` Zero fill left shift
- `>>` Signed right shift

### Operator Precedence
Parentheses → Exponentiation → Unary +/- → */% → +- → Comparisons → not → and → or

---

## **10. LISTS**

### List Basics
- Ordered, changeable, allows duplicates
- Created with square brackets

```python
mylist = ["apple", "banana", "cherry"]
```

### Access Items
```python
mylist[0]      # First item
mylist[-1]     # Last item
mylist[2:5]    # Range
```

### Change Items
```python
mylist[1] = "blackcurrant"
mylist[1:3] = ["watermelon", "mango"]
```

### Add Items
```python
mylist.append("orange")           # End
mylist.insert(1, "lemon")         # Specific position
mylist.extend(["kiwi", "papaya"]) # Add another list
```

### Remove Items
```python
mylist.remove("banana")
mylist.pop(1)       # Remove at index
mylist.pop()        # Remove last
del mylist[0]
mylist.clear()      # Empty list
```

### Loop Through List
```python
for x in mylist:
    print(x)
```

### List Comprehension
```python
newlist = [x for x in fruits if "a" in x]
```

### Sort Lists
```python
mylist.sort()            # Ascending
mylist.sort(reverse=True) # Descending
mylist.reverse()         # Reverse order
```

### Copy Lists
```python
newlist = mylist.copy()
newlist = list(mylist)
```

### Join Lists
```python
list3 = list1 + list2
list1.extend(list2)
```

### List Methods
- `append()`, `clear()`, `copy()`, `count()`
- `extend()`, `index()`, `insert()`, `pop()`
- `remove()`, `reverse()`, `sort()`

---

## **11. TUPLES**

### Tuple Basics
- Ordered, unchangeable, allows duplicates
- Created with parentheses

```python
mytuple = ("apple", "banana", "cherry")
```

### Access/Update
- Cannot change items directly
- Convert to list, modify, convert back

### Unpack Tuples
```python
(green, yellow, red) = mytuple
```

### Loop Through Tuple
```python
for x in mytuple:
    print(x)
```

### Join Tuples
```python
tuple3 = tuple1 + tuple2
```

### Tuple Methods
- `count()` - Count occurrences
- `index()` - Find index

---

## **12. SETS**

### Set Basics
- Unordered, unindexed, no duplicates
- Created with curly braces or `set()`

```python
myset = {"apple", "banana", "cherry"}
```

### Access Items
- Cannot access by index
- Loop through or check membership

### Add Items
```python
myset.add("orange")
myset.update({"mango", "grapes"})
```

### Remove Items
```python
myset.remove("banana")   # Error if not exists
myset.discard("banana")  # No error
myset.pop()              # Random item
myset.clear()
```

### Join Sets
```python
set3 = set1.union(set2)
set3 = set1 | set2
set1.update(set2)
```

### Set Methods
- `add()`, `clear()`, `copy()`
- `difference()`, `intersection()`
- `isdisjoint()`, `issubset()`, `issuperset()`
- `symmetric_difference()`, `union()`

### Frozenset
- Immutable version of set

---

## **13. DICTIONARIES**

### Dictionary Basics
- Ordered (Python 3.7+), changeable, no duplicates
- Key-value pairs

```python
mydict = {
    "brand": "Ford",
    "model": "Mustang",
    "year": 1964
}
```

### Access Items
```python
x = mydict["model"]
x = mydict.get("model")
keys = mydict.keys()
values = mydict.values()
items = mydict.items()
```

### Change Items
```python
mydict["year"] = 2020
mydict.update({"color": "red"})
```

### Add Items
```python
mydict["color"] = "red"
```

### Remove Items
```python
mydict.pop("model")
mydict.popitem()      # Removes last inserted
del mydict["model"]
del mydict            # Delete entire dict
mydict.clear()        # Empty dict
```

### Loop Through Dictionary
```python
for x in mydict:
    print(x)              # Keys
    
for x in mydict:
    print(mydict[x])      # Values
    
for x, y in mydict.items():
    print(x, y)           # Both
```

### Copy Dictionary
```python
mydict2 = mydict.copy()
mydict2 = dict(mydict)
```

### Nested Dictionaries
```python
myfamily = {
    "child1": {"name": "Emil", "year": 2004},
    "child2": {"name": "Tobias", "year": 2007}
}
```

### Dictionary Methods
- `clear()`, `copy()`, `fromkeys()`, `get()`
- `items()`, `keys()`, `pop()`, `popitem()`
- `setdefault()`, `update()`, `values()`

---

## **14. IF...ELSE**

### If Statement
```python
if b > a:
    print("b is greater than a")
```

### Elif
```python
if b > a:
    print("b is greater than a")
elif a == b:
    print("a and b are equal")
else:
    print("a is greater than b")
```

### Shorthand If
```python
if a > b: print("a is greater than b")
```

### Shorthand If...Else
```python
print("A") if a > b else print("B")
```

### And/Or
```python
if a > b and c > a:
    print("Both conditions are True")
    
if a > b or a > c:
    print("At least one condition is True")
```

### Nested If
```python
if x > 10:
    print("Above ten")
    if x > 20:
        print("and also above 20!")
```

### Pass Statement
```python
if b > a:
    pass  # Avoid error
```

---

## **15. MATCH (Switch-Case)**

```python
match status:
    case 200:
        print("OK")
    case 404:
        print("Not Found")
    case _:
        print("Unknown")
```

---

## **16. WHILE LOOPS**

```python
i = 1
while i < 6:
    print(i)
    i += 1
```

### Break Statement
```python
while i < 6:
    if i == 3:
        break
    i += 1
```

### Continue Statement
```python
while i < 6:
    i += 1
    if i == 3:
        continue
    print(i)
```

### Else in While
```python
while i < 6:
    print(i)
    i += 1
else:
    print("i is no longer less than 6")
```

---

## **17. FOR LOOPS**

```python
fruits = ["apple", "banana", "cherry"]
for x in fruits:
    print(x)
```

### Loop Through String
```python
for x in "banana":
    print(x)
```

### Break/Continue
Same as while loops

### Range Function
```python
for x in range(6):        # 0 to 5
    print(x)
    
for x in range(2, 6):     # 2 to 5
    print(x)
    
for x in range(2, 30, 3): # 2 to 29, step 3
    print(x)
```

### Else in For
```python
for x in range(6):
    print(x)
else:
    print("Finally finished!")
```

### Nested Loops
```python
for x in adj:
    for y in fruits:
        print(x, y)
```

### Pass Statement
```python
for x in [0, 1, 2]:
    pass
```

---

## **18. FUNCTIONS**

### Creating Functions
```python
def my_function():
    print("Hello from a function")
```

### Calling Functions
```python
my_function()
```

### Arguments/Parameters
```python
def my_function(fname):
    print(fname + " Refsnes")

my_function("Emil")
```

### Default Parameter Value
```python
def my_function(country="Norway"):
    print("I am from " + country)
```

### Return Values
```python
def my_function(x):
    return 5 * x
```

### *args (Arbitrary Arguments)
```python
def my_function(*kids):
    print("The youngest child is " + kids[2])
```

### **kwargs (Arbitrary Keyword Arguments)
```python
def my_function(**kid):
    print("His last name is " + kid["lname"])
```

### Scope
- **Local scope**: Inside function
- **Global scope**: Outside function
- Use `global` keyword to create/modify global variable inside function

### Lambda Functions
```python
x = lambda a : a + 10
print(x(5))  # 15

x = lambda a, b : a * b
print(x(5, 6))  # 30
```

### Recursion
```python
def tri_recursion(k):
    if(k > 0):
        result = k + tri_recursion(k - 1)
        print(result)
    else:
        result = 0
    return result
```

### Generators
```python
def my_generator():
    yield 1
    yield 2
    yield 3
```

---

## **19. ARRAYS**

Note: Python doesn't have built-in array support, but lists can be used. NumPy provides arrays.

---

## **20. ITERATORS**

```python
mytuple = ("apple", "banana", "cherry")
myit = iter(mytuple)

print(next(myit))  # apple
print(next(myit))  # banana
```

### Create Iterator
```python
class MyNumbers:
    def __iter__(self):
        self.a = 1
        return self
    
    def __next__(self):
        x = self.a
        self.a += 1
        return x
```

---

## **21. MODULES**

### Import Module
```python
import mymodule
mymodule.greeting("Jonathan")
```

### Import from Module
```python
from mymodule import person1
print(person1["age"])
```

### Built-in Modules
- `platform`, `math`, `random`, etc.

---

## **22. DATES**

```python
import datetime

x = datetime.datetime.now()
print(x.year)
print(x.strftime("%A"))  # Day name
print(x.strftime("%B"))  # Month name
```

### Date Formats
- `%Y` - Year (2026)
- `%m` - Month (01-12)
- `%d` - Day (01-31)
- `%H` - Hour (00-23)
- `%M` - Minute (00-59)
- `%S` - Second (00-59)

---

## **23. MATH**

### Built-in Math Functions
```python
x = min(5, 10, 25)   # 5
x = max(5, 10, 25)   # 25
x = abs(-7.25)       # 7.25
x = pow(4, 3)        # 64
```

### Math Module
```python
import math

x = math.sqrt(64)      # 8.0
x = math.ceil(1.4)     # 2
x = math.floor(1.4)    # 1
x = math.pi            # 3.141592653589793
```

---

## **24. JSON**

### Parse JSON
```python
import json

x = '{ "name":"John", "age":30 }'
y = json.loads(x)
print(y["age"])
```

### Convert to JSON
```python
import json

x = {
    "name": "John",
    "age": 30
}
y = json.dumps(x)
```

---

## **25. REGEX**

```python
import re

txt = "The rain in Spain"
x = re.search("^The.*Spain$", txt)
```

### Common Functions
- `findall()` - Returns list of all matches
- `search()` - Returns Match object
- `split()` - Splits string at matches
- `sub()` - Replaces matches

### Metacharacters
- `.` Any character
- `^` Starts with
- `$` Ends with
- `*` Zero or more
- `+` One or more
- `?` Zero or one
- `[]` Set of characters
- `|` Either/or

---

## **26. PIP**

Package manager for Python

```bash
pip install package_name
pip uninstall package_name
pip list
```

---

## **27. TRY...EXCEPT**

### Basic Exception Handling
```python
try:
    print(x)
except:
    print("An exception occurred")
```

### Multiple Exceptions
```python
try:
    print(x)
except NameError:
    print("Variable x is not defined")
except:
    print("Something else went wrong")
```

### Else Clause
```python
try:
    print("Hello")
except:
    print("Something went wrong")
else:
    print("Nothing went wrong")
```

### Finally Clause
```python
try:
    print(x)
except:
    print("Something went wrong")
finally:
    print("The try except is finished")
```

### Raise Exception
```python
x = -1
if x < 0:
    raise Exception("Sorry, no numbers below zero")
```

---

## **28. USER INPUT**

```python
username = input("Enter username:")
print("Username is: " + username)
```

---

## **29. VIRTUAL ENVIRONMENT**

```bash
pip install virtualenv
virtualenv myproject
source myproject/bin/activate  # Linux/Mac
myproject\Scripts\activate     # Windows
```

---

## **30. CLASSES/OBJECTS (OOP)**

### Create Class
```python
class MyClass:
    x = 5

p1 = MyClass()
print(p1.x)
```

### __init__() Method
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

p1 = Person("John", 36)
```

### Object Methods
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def myfunc(self):
        print("Hello my name is " + self.name)
```

### self Parameter
- Reference to current instance of class
- Must be first parameter in methods

### Modify Object Properties
```python
p1.age = 40
del p1.age
del p1
```

### Magic Methods
- `__str__()` - String representation
- `__repr__()` - Official string representation
- `__eq__()` - Equality comparison
- `__add__()` - Addition operator
- `__len__()` - Length
- `__lt__()` - Less than
- `__contains__()` - Membership test
- `__call__()` - Make object callable

---

## **31. INHERITANCE**

```python
class Student(Person):
    def __init__(self, fname, lname):
        super().__init__(fname, lname)
```

- Child class inherits from parent class
- Use `super()` to call parent methods

---

## **32. POLYMORPHISM**

```python
class Animal:
    def speak(self):
        pass

class Dog(Animal):
    def speak(self):
        return "Woof!"

class Cat(Animal):
    def speak(self):
        return "Meow!"
```

---

## **33. ENCAPULATION**

```python
class MyClass:
    def __init__(self):
        self.__private_var = 10  # Private variable
    
    def get_private(self):
        return self.__private_var
```

- Use `__` prefix for private attributes

---

## **34. FILE HANDLING**

### Open File
```python
f = open("demofile.txt", "r")
print(f.read())
f.close()
```

### File Modes
- `"r"` - Read (default)
- `"w"` - Write (overwrite)
- `"a"` - Append
- `"x"` - Create (error if exists)
- `"t"` - Text mode (default)
- `"b"` - Binary mode

### Read Files
```python
f = open("file.txt", "r")
print(f.read(5))      # Read 5 characters
print(f.readline())   # Read one line
for x in f:
    print(x)          # Loop through lines
f.close()
```

### Write/Create Files
```python
f = open("file.txt", "w")
f.write("Now the file has more content!")
f.close()
```

### Delete Files
```python
import os
os.remove("file.txt")
os.rmdir("folder")    # Remove empty folder
```

### File Methods
- `close()`, `read()`, `readline()`, `readlines()`
- `write()`, `writelines()`, `seek()`, `tell()`

---

## **35. NUMPY**

Numerical Python library for arrays and mathematical operations

---

## **36. PANDAS**

Data manipulation and analysis library

---

## **37. SCIPY**

Scientific computing library

---

## **38. DJANGO**

Web framework for Python

---

## **39. MATPLOTLIB**

Plotting and visualization library

- Pyplot interface
- Markers, Lines, Labels
- Grid, Subplots
- Scatter, Bars, Histograms, Pie Charts

---

## **40. MACHINE LEARNING**

### Topics Covered
- Mean, Median, Mode
- Standard Deviation, Percentile
- Data Distribution, Normal Distribution
- Scatter Plot
- Linear/Polynomial/Multiple Regression
- Train/Test Split
- Decision Tree
- Confusion Matrix
- Hierarchical Clustering
- Logistic Regression
- Grid Search
- K-means Clustering
- Cross Validation
- AUC-ROC Curve
- K-nearest neighbors

---

## **41. DATA STRUCTURES & ALGORITHMS**

### Data Structures
- Lists and Arrays
- Stacks
- Queues
- Linked Lists
- Hash Tables
- Trees (Binary Trees, BST, AVL Trees)
- Graphs

### Searching Algorithms
- Linear Search
- Binary Search

### Sorting Algorithms
- Bubble Sort
- Selection Sort
- Insertion Sort
- Quick Sort
- Counting Sort
- Radix Sort
- Merge Sort

---

## **42. DATABASES**

### MySQL
- Create Database/Table
- Insert, Select, Where, Order By
- Delete, Drop, Update
- Limit, Join

### MongoDB
- Create DB/Collection
- Insert, Find, Query
- Sort, Delete, Update
- Limit, Drop Collection

---

## **43. BUILT-IN FUNCTIONS REFERENCE**

### Common Functions
- `abs()`, `all()`, `any()`, `bin()`, `bool()`
- `chr()`, `dict()`, `dir()`, `enumerate()`
- `filter()`, `float()`, `format()`, `hex()`
- `input()`, `int()`, `isinstance()`, `len()`
- `list()`, `map()`, `max()`, `min()`
- `open()`, `ord()`, `pow()`, `print()`
- `range()`, `round()`, `set()`, `sorted()`
- `str()`, `sum()`, `tuple()`, `type()`, `zip()`

---

## **44. KEYWORDS**

`and`, `as`, `assert`, `async`, `await`, `break`, `case`, `class`, `continue`, `def`, `del`, `elif`, `else`, `except`, `False`, `finally`, `for`, `from`, `global`, `if`, `import`, `in`, `is`, `lambda`, `match`, `None`, `nonlocal`, `not`, `or`, `pass`, `raise`, `return`, `True`, `try`, `while`, `with`, `yield`

---

## **45. EXCEPTIONS**

Common exceptions:
- `ArithmeticError`, `AssertionError`, `AttributeError`
- `EOFError`, `ImportError`, `IndexError`
- `KeyError`, `MemoryError`, `NameError`
- `SyntaxError`, `TypeError`, `ValueError`
- `ZeroDivisionError`
