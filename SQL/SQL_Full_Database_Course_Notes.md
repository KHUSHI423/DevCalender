# SQL Tutorial – Full Database Course for Beginners
## Complete Notes from the Lecture Transcript

> **Source:** “SQL Tutorial - Full Database Course for Beginners” (Giraffe Academy transcript)  
> **Purpose:** Structured study notes covering the concepts and demonstrations in the transcript. The examples retain the course's MySQL-oriented syntax and terminology.

---

## 1. Database Fundamentals

### 1.1 What is a database?

A **database (DB)** is a collection of related information.

Examples:
- Phone book: names and phone numbers.
- Shopping list: products to purchase.
- To-do list: tasks.
- Social-media user base: user information.
- E-commerce platform: products, users, orders, reviews and prices.

A database does not have to be stored on a computer. It can be stored:
- On paper.
- In a person's memory.
- In a spreadsheet or text file.
- In a computer-based database system.

### 1.2 Why store data on computers?

Computer-based databases are useful when an application must manage large amounts of important information.

| Requirement | Small shopping list | Large application database |

| Amount of data | Small | Potentially millions or billions of records |
| Importance | Often convenient | May be essential to the application |
| Security | Usually low requirement | Important, especially for personal/payment data |
| Storage | Paper or memory may be enough | Computer-based storage and database software |

Computers make it easier to:
- Store and retrieve large amounts of information.
- Search and organize information.
- Control access and protect data.
- Back up and duplicate information.
- Make data available to software applications.

### 1.3 Database Management System (DBMS)

A **DBMS** is software used to create, maintain and manage databases.

It can:
- Create databases and tables.
- Insert, retrieve, update and delete data.
- Manage security, users and permissions.
- Back up, import and export information.
- Allow software applications to interact with stored data.

**Important distinction:**
- **Database:** the organized collection of data.
- **DBMS:** the software that manages that data.

An application generally communicates with the DBMS; the DBMS performs the database operations.

### 1.4 CRUD operations

CRUD describes the four fundamental operations performed on stored data.

| Letter | Operation | Meaning |
|---|---|---|
| C | Create | Add new information |
| R | Read / Retrieve | Get existing information |
| U | Update | Modify existing information |
| D | Delete | Remove information |

---

## 2. Types of Databases

### 2.1 Relational databases

A **relational database** organizes data into tables.

A table contains:
- **Rows:** individual records.
- **Columns:** attributes or fields describing each record.
- **Keys:** columns used to identify records and connect tables.

Each row is identified by a unique key. Relational databases are commonly called **SQL databases**.

The spreadsheet analogy is useful: a relational table resembles a spreadsheet with named columns and rows, but a relational database also defines data types, constraints and relationships.

### 2.2 Non-relational databases

A **non-relational database** is a database that does not organize its data using the relational table model. These are commonly called **NoSQL** or “not only SQL” databases.

The transcript introduces the broad distinction:
- Relational: data organized into tables with rows, columns and relationships.
- Non-relational: data represented using other structures rather than the traditional relational-table model.

### 2.3 Relational database management systems (RDBMS)

An **RDBMS** is a DBMS designed to manage relational databases.

Examples mentioned in the course:
- MySQL
- PostgreSQL
- Oracle
- Microsoft SQL Server

The course uses **MySQL** for demonstrations. The main learning objective is SQL and relational database concepts, rather than memorizing one particular MySQL interface.

---

## 3. Tables, Rows, Columns and Keys

### 3.1 Tables

A table stores information about one category of entity.

Example: a `student` table might contain:

| student_id | name | major |
|---:|---|---|
| 1 | Jack | Biology |
| 2 | Kate | Chemistry |
| 3 | Claire | Chemistry |

- `student` is the table name.
- `student_id`, `name` and `major` are columns.
- Each student entry is a row/record.

### 3.2 Primary key (PK)

A **primary key** uniquely identifies each row in a table.

Properties emphasized by the course:
- Each row must have a unique primary-key value.
- A primary key cannot be `NULL`.
- A table has one primary-key constraint, which may consist of one column or multiple columns.

Example:

```sql
CREATE TABLE student (
    student_id INT PRIMARY KEY,
    name VARCHAR(20),
    major VARCHAR(20)
);
```

Here, `student_id` identifies each student.

### 3.3 Foreign key (FK)

A **foreign key** is a column (or group of columns) in one table that refers to a key in another table.

Why use it?
- To represent relationships between tables.
- To connect related records.
- To help maintain referential integrity.

Example concept:
- `branch.branch_id` identifies a branch.
- `employee.branch_id` can refer to that branch.
- The employee's `branch_id` is a foreign key referencing the branch table.

### 3.4 Composite key

A **composite key** uses more than one column together to uniquely identify a row.

Example:

```sql
CREATE TABLE works_with (
    emp_id INT,
    client_id INT,
    total_sales INT,
    PRIMARY KEY (emp_id, client_id)
);
```

The pair `(emp_id, client_id)` identifies a particular employee-client relationship. Neither column necessarily identifies the relationship row by itself.

### 3.5 Keys at a glance

| Key | Purpose |
|---|---|
| Primary key | Uniquely identifies a row in its own table |
| Foreign key | Refers to a key in another (or the same) table |
| Composite key | Uses multiple columns together as a key |

---

## 4. SQL Fundamentals

### 4.1 What is SQL?

**SQL** stands for **Structured Query Language**. It is used to communicate with relational database management systems.

SQL can be used to:
- Create and manage databases.
- Define tables and database schemas.
- Insert, retrieve, update and delete records.
- Perform administrative tasks such as user and permission management.

SQL is used by multiple RDBMS products, including MySQL, PostgreSQL, Oracle and Microsoft SQL Server. Their implementations are similar in many areas, but some syntax and features differ.

### 4.2 Four broad categories of SQL

The course presents SQL as combining four broad language categories:

| Category | Full form | Main purpose | Typical operations |
|---|---|---|---|
| DQL | Data Query Language | Retrieve data | `SELECT` |
| DDL | Data Definition Language | Define database structures | `CREATE`, `ALTER`, `DROP` |
| DML | Data Manipulation Language | Change stored data | `INSERT`, `UPDATE`, `DELETE` |
| DCL | Data Control Language | Control access and permissions | `GRANT`, `REVOKE` |

The exact classification of commands can vary slightly across learning resources and database systems; the table reflects the broad grouping introduced in the lecture.

### 4.3 What is a query?

A **query** is a set of instructions, generally written in SQL, that tells the RDBMS what information to retrieve or what operation to perform.

The aim of a query is to obtain the required information rather than manually reading all records.

Example:

```sql
SELECT name, age
FROM employee
WHERE salary > 30000;
```

This requests the names and ages of employees whose salary is greater than 30,000.

---

## 5. Installing and Connecting to MySQL

The transcript demonstrates MySQL installation on Windows and Mac, then uses PopSQL as a graphical query editor.

### 5.1 Windows installation – course demonstration

The lecture's flow is:

1. Search for **MySQL Community Server** on the official MySQL developer site.
2. Download the MySQL Installer.
3. Accept the licence.
4. Choose the installation type. The demonstration uses a custom installation.
5. Select the MySQL Server and MySQL Shell components used in the course.
6. Execute the installation.
7. Configure the server using the installer defaults shown in the demonstration.
8. Create a password for the `root` administrative account.
9. Finish the server configuration.
10. Open the MySQL command-line client.
11. Enter the root password to connect to the local server.
12. Create the practice database:

```sql
CREATE DATABASE giraffe;
```

> The transcript uses an intentionally simple example password during the demonstration. Do **not** reuse a weak demonstration password for a real system.

### 5.2 Mac installation – course demonstration

The lecture demonstrates installing the MySQL package on macOS and starting the local MySQL server.

General flow shown:
1. Download the MySQL package for macOS.
2. Run the package installer and follow the installation steps.
3. Note the temporary/root password supplied during setup.
4. Start the MySQL server.
5. Open Terminal and connect to MySQL using the MySQL command-line client.
6. Change the temporary root password.
7. Create the `giraffe` database.
8. Connect a query editor to the local MySQL server.

The exact screens and setup details are specific to the version shown in the lecture.

### 5.3 MySQL server vs query editor

- **MySQL Server:** the database server that stores and manages the databases.
- **MySQL command-line client:** a terminal interface for sending SQL commands to MySQL.
- **PopSQL:** the graphical SQL editor used in the demonstration to write queries and view results.

PopSQL is not the database itself. It connects to the MySQL server.

### 5.4 Typical connection details in the demonstration

| Setting | Meaning |
|---|---|
| Host | `localhost` for a database server running on the same computer |
| Port | MySQL's configured server port |
| User | The MySQL account, such as `root` |
| Password | Password configured for that account |
| Database | The database to open, such as `giraffe` |

---

## 6. Creating and Managing Tables

### 6.1 Create a database

```sql
CREATE DATABASE database_name;
```

Example:

```sql
CREATE DATABASE giraffe;
```

### 6.2 Select a database

```sql
USE database_name;
```

Example:

```sql
USE giraffe;
```

This makes `giraffe` the active database for subsequent commands in the session.

### 6.3 Create a table

General structure:

```sql
CREATE TABLE table_name (
    column_name data_type,
    column_name data_type,
    ...
);
```

Example from the student-table exercise:

```sql
CREATE TABLE student (
    student_id INT PRIMARY KEY,
    name VARCHAR(20),
    major VARCHAR(20)
);
```

### 6.4 Common data types introduced

| Data type | Use |
|---|---|
| `INT` | Whole numbers |
| `DECIMAL(p,s)` | Numeric values with a defined precision and scale |
| `VARCHAR(n)` | Variable-length text up to a specified length |
| `DATE` | Date values |
| `CHAR(n)` | Fixed-length text |
| `FLOAT` / `DOUBLE` | Approximate numeric values |

The lecture's examples primarily use `INT`, `VARCHAR` and `DATE`.

### 6.5 `DESCRIBE`

Use `DESCRIBE` to inspect a table's structure.

```sql
DESCRIBE student;
```

It displays information such as:
- Column names.
- Data types.
- Whether `NULL` is allowed.
- Key information.
- Default values and other column details.

### 6.6 Drop a table

```sql
DROP TABLE table_name;
```

Example:

```sql
DROP TABLE student;
```

This removes the table and its stored data. It is a destructive operation.

### 6.7 Alter a table

`ALTER TABLE` changes the structure of an existing table.

Examples of changes covered in the course include adding or modifying columns and adding constraints.

```sql
ALTER TABLE student
ADD gpa DECIMAL(3,2);
```

To add a foreign-key constraint after the related tables exist:

```sql
ALTER TABLE employee
ADD FOREIGN KEY (branch_id)
REFERENCES branch(branch_id);
```

The lecture uses `ALTER TABLE` when a relationship cannot be declared at the initial table-creation stage because the referenced table has not yet been created.

---

## 7. Inserting Data

### 7.1 Insert a complete row

```sql
INSERT INTO student
VALUES (1, 'Jack', 'Biology');
```

The values must match the table's column order and compatible data types.

### 7.2 Insert into selected columns

```sql
INSERT INTO student (student_id, name)
VALUES (2, 'Kate');
```

Columns omitted from the insert must be allowed to take a default value or `NULL`, or the database must otherwise be able to supply a value.

### 7.3 Insert multiple rows

```sql
INSERT INTO student
VALUES
    (1, 'Jack', 'Biology'),
    (2, 'Kate', 'Chemistry'),
    (3, 'Claire', 'Chemistry');
```

Multiple records can be inserted with one statement.

### 7.4 Important reminders

- Text values are written inside quotes.
- Numeric values are generally not quoted.
- Values must match the target columns.
- The number of values must match the number of specified columns.
- A primary-key value must be unique and non-`NULL`.

---

## 8. Updating and Deleting Data

### 8.1 Update records

General syntax:

```sql
UPDATE table_name
SET column_name = value
WHERE condition;
```

Example:

```sql
UPDATE student
SET major = 'Biochemistry'
WHERE major = 'Biology';
```

The `WHERE` clause determines which rows are changed.

**Important:** If `WHERE` is omitted, the update applies to every row in the table.

### 8.2 Update multiple columns

```sql
UPDATE student
SET name = 'Jack Smith',
    major = 'Biology'
WHERE student_id = 1;
```

### 8.3 Delete records

```sql
DELETE FROM student
WHERE student_id = 2;
```

This deletes the row matching the condition.

**Important:** If `WHERE` is omitted, all rows in the table are deleted.

### 8.4 Difference: DELETE vs DROP

| Command | What it removes |
|---|---|
| `DELETE FROM table_name ...` | Rows from a table |
| `DROP TABLE table_name` | The table structure and its data |

---

## 9. Basic SELECT Queries

`SELECT` retrieves data from a table.

### 9.1 Retrieve every column

```sql
SELECT *
FROM student;
```

`*` means all columns.

### 9.2 Retrieve selected columns

```sql
SELECT name, major
FROM student;
```

Only the requested columns are returned.

### 9.3 Limit the number of rows

```sql
SELECT *
FROM student
LIMIT 2;
```

This returns at most two rows.

### 9.4 Sort results with ORDER BY

```sql
SELECT *
FROM student
ORDER BY student_id;
```

Ascending order is the default in the demonstration.

```sql
SELECT *
FROM student
ORDER BY student_id DESC;
```

`DESC` sorts in descending order; `ASC` sorts in ascending order.

### 9.5 Combine ORDER BY and LIMIT

```sql
SELECT *
FROM student
ORDER BY student_id DESC
LIMIT 2;
```

The rows are ordered by descending `student_id`, and then the first two rows are returned.

### 9.6 Filter rows with WHERE

```sql
SELECT *
FROM student
WHERE major = 'Biology';
```

Only rows satisfying the condition are returned.

### 9.7 Comparison operators

| Operator | Meaning |
|---|---|
| `=` | Equal to |
| `!=` or `<>` | Not equal to |
| `<` | Less than |
| `>` | Greater than |
| `<=` | Less than or equal to |
| `>=` | Greater than or equal to |

Examples:

```sql
SELECT *
FROM student
WHERE major != 'Chemistry';

SELECT *
FROM student
WHERE student_id < 3;
```

### 9.8 Combine conditions with AND / OR

```sql
SELECT *
FROM student
WHERE major = 'Chemistry'
   OR major = 'Biology';
```

```sql
SELECT *
FROM student
WHERE major = 'Chemistry'
  AND student_id > 2;
```

- `AND`: every condition must be true.
- `OR`: at least one condition must be true.

Use parentheses when combining several `AND` and `OR` conditions to make the intended logic clear.

### 9.9 SQL comments

The transcript demonstrates a two-dash comment:

```sql
-- This is a comment
SELECT * FROM student;
```

---

## 10. The Company Database Schema

The course moves from the small `student` table to a more realistic company database so that more complex queries and relationships can be demonstrated.

### 10.1 Main tables

The company schema includes the following tables:

| Table | Stores |
|---|---|
| `employee` | Employee details |
| `branch` | Company branch details |
| `client` | Client details |
| `works_with` | Sales/working relationships between employees and clients |
| `branch_supplier` | Suppliers associated with branches |

### 10.2 Employee table

The employee table stores details such as:
- `emp_id`
- `first_name`
- `last_name`
- `birth_day`
- `sex`
- `salary`
- `super_id` – supervisor's employee ID
- `branch_id` – branch where the employee works

`emp_id` is the primary key. `super_id` and `branch_id` represent relationships to other records.

### 10.3 Branch table

The branch table stores:
- `branch_id`
- `branch_name`
- `mgr_id` – employee who manages the branch
- `mgr_start_date` – date the employee began managing the branch

`branch_id` is the primary key. `mgr_id` refers to an employee.

### 10.4 Client table

The client table stores:
- `client_id`
- `client_name`
- `branch_id`

`client_id` identifies a client. `branch_id` refers to the branch handling the client.

### 10.5 Works_With table

This table represents which employees work with which clients and the amount of sales.

It includes:
- `emp_id`
- `client_id`
- `total_sales`

The combination of `emp_id` and `client_id` is used as a composite primary key. The two columns are also foreign keys.

### 10.6 Branch_Supplier table

This table records suppliers associated with branches. The lecture uses a composite key made from branch and supplier-identifying information, including supplier name and supply type.

### 10.7 Why the company schema matters

The schema demonstrates:
- One table can contain a primary key and multiple foreign keys.
- A foreign key can refer to another table.
- A table can use a composite primary key.
- A relationship can have its own attribute, such as `total_sales`.
- Related information is split across tables instead of being duplicated in one large table.

---

## 11. More SELECT Query Techniques

The company database is used to practise filtering, sorting, selecting columns and combining conditions.

### 11.1 Select particular columns

```sql
SELECT first_name, last_name
FROM employee;
```

### 11.2 Filter with WHERE

```sql
SELECT *
FROM employee
WHERE sex = 'F';
```

### 11.3 Sort and limit

```sql
SELECT *
FROM employee
ORDER BY salary DESC
LIMIT 5;
```

This returns the first five rows after sorting by salary from highest to lowest.

### 11.4 Use multiple conditions

```sql
SELECT *
FROM employee
WHERE sex = 'F'
  AND salary > 50000;
```

Read the query in this order:
1. Identify the table.
2. Apply the condition in `WHERE`.
3. Return the requested columns.

---

## 12. SQL Functions and Aggregation

Functions allow calculations to be performed on data.

The lecture demonstrates common aggregate functions on numeric columns.

| Function | Purpose |
|---|---|
| `COUNT()` | Counts rows or non-`NULL` values, depending on the expression |
| `SUM()` | Adds numeric values |
| `AVG()` | Calculates the average |
| `MAX()` | Returns the maximum value |
| `MIN()` | Returns the minimum value |

Examples:

```sql
SELECT COUNT(emp_id)
FROM employee;
```

```sql
SELECT SUM(salary)
FROM employee;
```

```sql
SELECT AVG(salary)
FROM employee;
```

```sql
SELECT MAX(salary)
FROM employee;
```

```sql
SELECT MIN(salary)
FROM employee;
```

### 12.1 COUNT with a condition

```sql
SELECT COUNT(emp_id)
FROM employee
WHERE sex = 'F';
```

This counts employees satisfying the filter.

### 12.2 Combining functions with filters

```sql
SELECT AVG(salary)
FROM employee
WHERE sex = 'M';
```

The `WHERE` condition first limits the rows considered by the aggregate.

---

## 13. Wildcards and LIKE

`LIKE` is used in a `WHERE` clause to search for text patterns.

The course introduces two important wildcard characters:

| Wildcard | Meaning |
|---|---|
| `%` | Zero or more characters |
| `_` | Exactly one character |

Examples:

```sql
-- Names beginning with 'a'
SELECT *
FROM employee
WHERE first_name LIKE 'a%';
```

```sql
-- Names ending with 'n'
SELECT *
FROM employee
WHERE first_name LIKE '%n';
```

```sql
-- Names containing 'an'
SELECT *
FROM employee
WHERE first_name LIKE '%an%';
```

```sql
-- A pattern with one character in a specific position
SELECT *
FROM employee
WHERE first_name LIKE '_a%';
```

Remember:
- `%` can match a string of any length, including an empty string.
- `_` matches one character.
- `LIKE` is useful when the exact text value is not known.

---

## 14. UNION

`UNION` combines the result sets of multiple `SELECT` statements into one result.

Example:

```sql
SELECT first_name
FROM employee
UNION
SELECT branch_name
FROM branch;
```

Requirements:
- Each `SELECT` must return the same number of columns.
- Corresponding columns should have compatible data types.
- The columns must be in corresponding positions.

`UNION` removes duplicate rows from the combined result.

The related operator `UNION ALL` retains duplicates:

```sql
SELECT first_name
FROM employee
UNION ALL
SELECT branch_name
FROM branch;
```

The lecture's central point is that `UNION` combines compatible query results vertically; it is not the same as joining tables side by side.

---

## 15. JOINS

A **JOIN** combines related rows from multiple tables using a relationship or matching condition.

### 15.1 Why joins are needed

Related data is stored in separate tables. A join allows the query to retrieve related information together.

Example: an employee record contains a branch ID, while the branch name is stored in the branch table. A join can return the employee and branch information together.

### 15.2 INNER JOIN

Returns rows where the join condition matches in both tables.

```sql
SELECT employee.emp_id,
       employee.first_name,
       branch.branch_name
FROM employee
JOIN branch
  ON employee.branch_id = branch.branch_id;
```

Only matching employee-branch pairs appear.

### 15.3 LEFT JOIN

Returns:
- Every row from the left table.
- Matching rows from the right table.
- `NULL` for right-table columns when there is no match.

```sql
SELECT employee.first_name,
       branch.branch_name
FROM employee
LEFT JOIN branch
  ON employee.branch_id = branch.branch_id;
```

### 15.4 RIGHT JOIN

Returns:
- Every row from the right table.
- Matching rows from the left table.
- `NULL` for left-table columns when there is no match.

```sql
SELECT employee.first_name,
       branch.branch_name
FROM employee
RIGHT JOIN branch
  ON employee.branch_id = branch.branch_id;
```

### 15.5 Joining a table to itself (self join)

A self join uses the same table twice, usually with aliases.

The company database has a supervisor relationship: an employee's `super_id` refers to another employee's `emp_id`.

```sql
SELECT e.first_name AS employee,
       s.first_name AS supervisor
FROM employee AS e
LEFT JOIN employee AS s
  ON e.super_id = s.emp_id;
```

Here:
- `e` represents the employee.
- `s` represents the supervisor.
- Both aliases refer to the `employee` table.

### 15.6 Join comparison

| Join | Rows retained |
|---|---|
| `INNER JOIN` | Only matching rows from both sides |
| `LEFT JOIN` | All left rows, with matching right rows where available |
| `RIGHT JOIN` | All right rows, with matching left rows where available |
| Self join | A table joined to another reference of itself |

---

## 16. Nested Queries (Subqueries)

A **nested query**, or **subquery**, is a query placed inside another SQL query.

The inner query produces a result that the outer query uses.

Example pattern:

```sql
SELECT column_name
FROM table_name
WHERE column_name IN (
    SELECT column_name
    FROM another_table
    WHERE condition
);
```

A company-database example can use a subquery to find employees who work with a particular client:

```sql
SELECT first_name, last_name
FROM employee
WHERE emp_id IN (
    SELECT emp_id
    FROM works_with
    WHERE client_id = 3
);
```

Conceptual execution:
1. The inner query finds the relevant employee IDs in `works_with`.
2. The outer query finds employee records with those IDs.
3. The final result contains employee information.

### 16.1 IN

`IN` checks whether a value matches any value in a list or subquery result.

```sql
SELECT *
FROM employee
WHERE emp_id IN (1, 2, 3);
```

### 16.2 When nested queries help

Use a subquery when:
- The condition depends on data retrieved from another query.
- You need to find IDs or values first, then retrieve associated records.
- The query is easier to express as an inner result followed by an outer query.

---

## 17. ON DELETE: Foreign-Key Actions

A foreign key enforces a relationship between records. The lecture introduces actions that determine what happens to referencing rows when a referenced row is deleted.

### 17.1 ON DELETE SET NULL

```sql
FOREIGN KEY (branch_id)
REFERENCES branch(branch_id)
ON DELETE SET NULL
```

When the referenced branch is deleted, the referencing foreign-key value is set to `NULL` (where the column permits `NULL`).

### 17.2 ON DELETE CASCADE

```sql
FOREIGN KEY (branch_id)
REFERENCES branch(branch_id)
ON DELETE CASCADE
```

When the referenced row is deleted, related rows referencing it are also deleted.

### 17.3 Comparison

| Action | Effect when referenced parent row is deleted |
|---|---|
| `SET NULL` | Sets the referencing foreign-key value to `NULL` |
| `CASCADE` | Deletes the referencing row(s) |

Choose the action based on the intended data relationship. `CASCADE` can delete more data than expected, so it should be used carefully.

### 17.4 Adding foreign keys after table creation

The lecture demonstrates adding a foreign key with `ALTER TABLE`:

```sql
ALTER TABLE employee
ADD FOREIGN KEY (branch_id)
REFERENCES branch(branch_id)
ON DELETE SET NULL;
```

This is useful when tables must be created in an order that makes it impossible to declare every relationship immediately.

---

## 18. Triggers

A **trigger** is a database action that runs automatically when a specified event occurs on a table.

The lecture introduces triggers as a way to automate an operation in response to an event such as an insert, update or delete.

### 18.1 Trigger structure (MySQL-style example)

```sql
CREATE TRIGGER trigger_name
trigger_time trigger_event
ON table_name
FOR EACH ROW
BEGIN
    -- statements to execute
END;
```

Key parts:
- Trigger name.
- Timing: `BEFORE` or `AFTER`.
- Event: `INSERT`, `UPDATE` or `DELETE`.
- Table on which the trigger is defined.
- Statements executed for each affected row.

### 18.2 Example idea

A trigger could automatically update a related record or perform a check when a row is inserted.

```sql
CREATE TRIGGER example_trigger
BEFORE INSERT ON employee
FOR EACH ROW
BEGIN
    -- validation or automatic action
END;
```

The exact body must contain valid SQL for the intended task. The main concept is that the database invokes the trigger automatically when its event occurs.

---

## 19. ER Diagrams – Introduction

An **Entity-Relationship (ER) diagram** is a visual representation of:
- Entities.
- Their attributes.
- Relationships between entities.
- Cardinality and participation constraints.

It acts as a bridge between high-level data requirements and a relational database schema.

### 19.1 Entity

An **entity** is an object or concept about which the system stores information.

Examples:
- Employee
- Branch
- Client
- Class
- Exam

In the notation used in the lecture:
- Entity: rectangle.
- Weak entity: double rectangle.

### 19.2 Attributes

An **attribute** is a property of an entity or relationship.

Examples:
- Employee: employee ID, first name, last name, birth date, sex, salary.
- Branch: branch ID, branch name.
- Client: client ID, client name.

Common notation introduced:
- Attribute: oval.
- Key attribute: underlined.
- Multivalued attribute: double oval.
- Derived attribute: dashed oval.
- Relationship attribute: attached to the relationship.

### 19.3 Relationship

A **relationship** describes an association between entities. It is commonly named using a verb.

Examples:
- Employee **works for** Branch.
- Employee **manages** Branch.
- Branch **handles** Client.
- Employee **works with** Client.

In the lecture's notation, a relationship is represented by a diamond.

### 19.4 Cardinality

Cardinality describes how many instances of one entity can be associated with instances of another entity.

| Relationship | Meaning |
|---|---|
| 1:1 | One instance relates to at most one instance on the other side |
| 1:N | One instance can relate to many instances on the other side |
| M:N | Many instances on either side can relate to many on the other side |

Examples:
- One branch can have many employees; each employee works for one branch: 1:N.
- A branch can handle many clients; each client is handled by one branch: 1:N.
- Employees can work with many clients, and clients can work with many employees: M:N.

### 19.5 Participation constraints

Participation describes whether participation in a relationship is mandatory.

- **Total participation:** every entity instance must participate in the relationship. The lecture represents it with a double line.
- **Partial participation:** participation is optional. The lecture represents it with a single line.

Examples from the company model:
- Every branch must have employees working for it (as assumed in the lecture's diagram).
- Every employee works for a branch (as assumed in the diagram).
- Every branch has a manager.
- Not every employee has to manage a branch.
- Every client is handled by a branch.
- A branch may or may not handle clients.

The transcript points out that some participation assumptions are design decisions when the requirements do not explicitly specify them.

### 19.6 Weak entities

A **weak entity** cannot be uniquely identified by its own attributes alone. It depends on an owner entity.

Example used in the lecture:
- An exam is associated with a class.
- An exam cannot exist independently of its class in this model.

Notation introduced:
- Weak entity: double rectangle.
- Identifying relationship: double diamond.
- Weak entity has total participation in its identifying relationship.
- A partial key helps distinguish weak entities belonging to the same owner.

### 19.7 Recursive (unary) relationship

A recursive relationship occurs when an entity has a relationship with itself.

Example:
- An employee supervises another employee.
- Both roles are instances of the `employee` entity.

The employee table can represent this with `super_id` referencing `emp_id`.

---

## 20. Designing an ER Diagram from Requirements

The lecture demonstrates converting a written company requirements document into an ER diagram.

### 20.1 Company requirements described in the lecture

The document states, in summary:
- The company is organized into branches.
- Each branch has a unique number and a name.
- Each branch has an employee who manages it.
- The company sells to clients.
- Each client has a unique number and a name.
- Each employee has a unique number, name, birthday, sex and salary.
- An employee works for one branch at a time.
- A branch is managed by one of its employees.
- The manager's start date must be recorded.
- Employees can supervise other employees.
- A supervisor can supervise employees in other branches.
- An employee has at most one supervisor.
- A branch can handle multiple clients.
- A client is handled by one branch at a time.
- Employee-client working relationships and sales information are represented.

### 20.2 Identify entities first

The main entities are:
1. Employee
2. Branch
3. Client

Identify attributes and keys:
- Employee: `emp_id` and employee details.
- Branch: `branch_id`, branch name.
- Client: `client_id`, client name.

A phrase such as “unique number” is a clue that the attribute can be used as a key.

### 20.3 Add relationships

Translate verbs and requirements into relationships:
- Employee **works for** Branch.
- Employee **manages** Branch.
- Employee **supervises** Employee.
- Branch **handles** Client.
- Employee **works with** Client.

### 20.4 Add relationship attributes

Some information belongs to the relationship rather than to either entity alone.

Examples:
- `manager_start_date` belongs to the Employee-Manages-Branch relationship in the conceptual model.
- `total_sales` belongs to the Employee-Works_With-Client relationship.

### 20.5 Add cardinality and participation

Use the requirements to determine:
- One-to-one.
- One-to-many.
- Many-to-many.
- Total participation.
- Partial participation.

Do not assume every relationship is mandatory. Where the requirements do not specify participation, the designer may need to make and document an assumption.

---

## 21. Converting ER Diagrams into Relational Schemas

A **relational schema** describes the tables, columns and keys used to implement the data model.

The lecture walks through mapping entities and relationships into tables.

### Rule 1: Strong entity

Create one relation (table) for each strong entity.

Include:
- All simple attributes.
- The entity's primary key.

Example:

```text
EMPLOYEE(
    emp_id PK,
    first_name,
    last_name,
    birth_date,
    sex,
    salary
)
```

### Rule 2: Weak entity

Create a relation for the weak entity.

Include:
- Its attributes.
- The primary key of its owner entity as a foreign key.
- A primary key formed from the owner's primary key plus the weak entity's partial key.

General idea:

```text
WEAK_ENTITY(
    owner_id FK,
    partial_key,
    other_attributes,
    PK(owner_id, partial_key)
)
```

### Rule 3: One-to-one (1:1) relationship

For a 1:1 relationship, place one entity's primary key as a foreign key in the other entity's relation.

The lecture's mapping guidance considers participation:
- If one side has total participation, place the foreign key on that side where appropriate.
- Include any attributes belonging to the relationship in the selected relation.

### Rule 4: One-to-many (1:N) relationship

Place the primary key from the **one** side as a foreign key in the relation on the **many** side.

Examples:
- One branch has many employees → store `branch_id` as a foreign key in `employee`.
- One branch handles many clients → store `branch_id` as a foreign key in `client`.

This is one of the most important mapping rules to remember.

### Rule 5: Many-to-many (M:N) relationship

Create a new relation for the relationship.

Include:
- The primary key of the first entity as a foreign key.
- The primary key of the second entity as a foreign key.
- Any attributes belonging to the relationship.

Usually, the combination of the two foreign keys forms the composite primary key.

Example:

```text
WORKS_WITH(
    emp_id FK,
    client_id FK,
    total_sales,
    PK(emp_id, client_id)
)
```

### 21.1 Mapping the company example

A simplified relational design is:

```text
EMPLOYEE(
    emp_id PK,
    first_name,
    last_name,
    birth_date,
    sex,
    salary,
    super_id FK -> EMPLOYEE.emp_id,
    branch_id FK -> BRANCH.branch_id
)

BRANCH(
    branch_id PK,
    branch_name,
    mgr_id FK -> EMPLOYEE.emp_id,
    mgr_start_date
)

CLIENT(
    client_id PK,
    client_name,
    branch_id FK -> BRANCH.branch_id
)

WORKS_WITH(
    emp_id FK -> EMPLOYEE.emp_id,
    client_id FK -> CLIENT.client_id,
    total_sales,
    PK(emp_id, client_id)
)
```

The supplier relationship is represented separately in the `branch_supplier` relation, using the branch and supplier-identifying attributes described in the lecture.

### 21.2 Why ER diagrams are useful

An ER diagram:
- Turns written requirements into a visual model.
- Makes entities and relationships easier to inspect.
- Helps identify keys and constraints before writing SQL.
- Provides a middle step between requirements and actual table creation.
- Helps prevent missing or incorrectly represented relationships.

---

## 22. Important SQL Syntax – Quick Reference

| Task | Syntax |
|---|---|
| Create database | `CREATE DATABASE db_name;` |
| Select database | `USE db_name;` |
| Create table | `CREATE TABLE t (...);` |
| Inspect table | `DESCRIBE t;` |
| Insert row | `INSERT INTO t VALUES (...);` |
| Read all columns | `SELECT * FROM t;` |
| Read selected columns | `SELECT c1, c2 FROM t;` |
| Filter | `SELECT * FROM t WHERE condition;` |
| Sort ascending | `ORDER BY column ASC` |
| Sort descending | `ORDER BY column DESC` |
| Limit rows | `LIMIT n` |
| Update | `UPDATE t SET c = value WHERE condition;` |
| Delete rows | `DELETE FROM t WHERE condition;` |
| Add a column | `ALTER TABLE t ADD column_name data_type;` |
| Add a foreign key | `ALTER TABLE t ADD FOREIGN KEY (col) REFERENCES other_table(key);` |
| Drop table | `DROP TABLE t;` |
| Join tables | `SELECT ... FROM a JOIN b ON a.key = b.key;` |
| Pattern search | `WHERE column LIKE 'pattern'` |
| Combine results | `SELECT ... UNION SELECT ...` |
| Count | `SELECT COUNT(*) FROM t;` |
| Average | `SELECT AVG(column) FROM t;` |
| Sum | `SELECT SUM(column) FROM t;` |
| Maximum | `SELECT MAX(column) FROM t;` |
| Minimum | `SELECT MIN(column) FROM t;` |

---

## 23. Common Mistakes to Avoid

1. **Forgetting `WHERE` in `UPDATE`:** this may update every row.
2. **Forgetting `WHERE` in `DELETE`:** this may delete every row.
3. **Confusing `DELETE` and `DROP`:** one removes rows; the other removes the table itself.
4. **Using a non-unique primary key:** primary keys must uniquely identify records.
5. **Inserting values in the wrong order:** specify the column list when the order is not obvious.
6. **Creating a foreign key before its referenced table exists:** create tables in a suitable order or add the constraint later with `ALTER TABLE`.
7. **Joining on the wrong columns:** use the columns that represent the actual relationship.
8. **Using `UNION` when a JOIN is required:** `UNION` stacks compatible result sets; JOIN combines related columns from rows.
9. **Confusing `%` and `_`:** `%` matches zero or more characters; `_` matches one character.
10. **Using `ON DELETE CASCADE` without considering its impact:** deleting a parent row can delete related child rows.
11. **Forgetting that aggregate functions operate on the filtered result:** a `WHERE` clause limits the rows considered.
12. **Assuming every SQL feature is identical across RDBMS products:** core concepts are shared, but syntax and behaviour can differ.

---

## 24. Revision Checklist

Use this checklist to test whether you understand the full lecture.

- [ ] Define database, DBMS and RDBMS.
- [ ] Explain why applications use database management systems.
- [ ] Explain CRUD.
- [ ] Distinguish relational and non-relational databases.
- [ ] Explain tables, rows, columns and data types.
- [ ] Distinguish primary, foreign and composite keys.
- [ ] Explain what SQL is and what a query does.
- [ ] Distinguish DQL, DDL, DML and DCL.
- [ ] Create and select a database.
- [ ] Create, describe, alter and drop a table.
- [ ] Insert one row and multiple rows.
- [ ] Update and delete selected records safely.
- [ ] Write `SELECT`, `WHERE`, `ORDER BY` and `LIMIT` queries.
- [ ] Use comparison operators, `AND` and `OR`.
- [ ] Use `COUNT`, `SUM`, `AVG`, `MAX` and `MIN`.
- [ ] Use `LIKE` with `%` and `_`.
- [ ] Explain and write a `UNION`.
- [ ] Distinguish INNER, LEFT and RIGHT JOIN.
- [ ] Write a self join for employee-supervisor data.
- [ ] Explain and write a nested query.
- [ ] Distinguish `ON DELETE SET NULL` and `ON DELETE CASCADE`.
- [ ] Explain what a trigger does.
- [ ] Identify entities, attributes and relationships in an ER diagram.
- [ ] Explain cardinality and participation.
- [ ] Explain weak entities and identifying relationships.
- [ ] Convert strong entities, weak entities and 1:1, 1:N and M:N relationships into tables.

---

## 25. Final Concept Map

```text
DATABASE
  └── DBMS
       └── RDBMS (e.g., MySQL)
            ├── DATABASE / SCHEMA
            │    ├── TABLES
            │    │    ├── ROWS
            │    │    ├── COLUMNS
            │    │    └── DATA TYPES
            │    └── RELATIONSHIPS
            │         ├── PRIMARY KEY
            │         ├── FOREIGN KEY
            │         └── COMPOSITE KEY
            │
            └── SQL
                 ├── DQL: SELECT
                 ├── DDL: CREATE, ALTER, DROP
                 ├── DML: INSERT, UPDATE, DELETE
                 ├── DCL: permissions / access
                 └── Query techniques
                      ├── WHERE, ORDER BY, LIMIT
                      ├── Functions
                      ├── LIKE / wildcards
                      ├── UNION
                      ├── JOIN
                      └── Subqueries

DATABASE DESIGN
  └── Requirements
       └── ER Diagram
            ├── Entities
            ├── Attributes
            ├── Relationships
            ├── Cardinality
            └── Participation
                 └── Relational Schema / Tables
```

**Core takeaway:** SQL is the language used to work with relational databases. Keys connect tables, queries retrieve and manipulate data, and ER diagrams help translate real-world requirements into a relational schema.
