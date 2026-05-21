
# Database

## Q1. What is a Database?

A database is an organized collection of related data stored electronically for easy access, management and retrieval.

### Example

Student database:

|RollNo|Name|Dept|
|---|---|---|
|101|Arun|CSE|
|102|Neha|ECE|

---

## Q2. What are the advantages of Database?

- Easy data access
    
- Reduced redundancy
    
- Better security
    
- Data consistency
    
- Multi-user support
    

---

## Q3. Difference between Database and DBMS

|Database|DBMS|
|---|---|
|Collection of data|Software used to manage database|

---

# DBMS

## Q1. What is DBMS?

DBMS (Database Management System) is software used to create, manage and manipulate databases.

Examples:

- MySQL
    
- Oracle
    
- PostgreSQL
    

---

## Q2. Advantages of DBMS

- Reduces redundancy
    
- Provides security
    
- Backup and recovery
    
- Multiple user access
    
- Data integrity
    

---

## Q3. What is data redundancy?

Duplicate copies of same data stored in multiple places.

---

## Q4. What is data inconsistency?

When same data has different values in different places.

---

# CREATE Command

## Q1. What is CREATE command?

CREATE command is used to create database objects like database, table and view.

It belongs to DDL.

---

## Syntax

```sql
CREATE TABLE student(
    rollno INT,
    name VARCHAR(30)
);
```

---

## Example

```sql
CREATE TABLE Employee(
    empid INT,
    empname VARCHAR(30),
    salary INT
);
```

---

## Important Viva Questions

### Which language category does CREATE belong to?

DDL.

### Difference between CREATE and INSERT

|CREATE|INSERT|
|---|---|
|Creates structure|Adds records|

---

# Table Creation

## Syntax

```sql
CREATE TABLE table_name(
    column_name datatype,
    column_name datatype
);
```

---

## Example

```sql
CREATE TABLE Student(
    rollno INT PRIMARY KEY,
    name VARCHAR(30),
    dept VARCHAR(10)
);
```

---

## Important Datatypes

|Datatype|Purpose|
|---|---|
|INT|Integer numbers|
|VARCHAR|Variable text|
|CHAR|Fixed text|
|FLOAT|Decimal values|
|DATE|Dates|

---

# Datatypes

## INT

Stores integer values.

Example:

```sql
marks INT
```

---

## VARCHAR

Stores variable-length text.

```sql
name VARCHAR(30)
```

---

## CHAR

Stores fixed-length text.

```sql
gender CHAR(1)
```

---

## FLOAT

Stores decimal values.

```sql
salary FLOAT
```

---

## DATE

Stores date values.

```sql
dob DATE
```

---

## Difference Between CHAR and VARCHAR

|CHAR|VARCHAR|
|---|---|
|Fixed size|Variable size|

---

# SHOW Commands

## SHOW DATABASES

Displays all databases.

```sql
SHOW DATABASES;
```

---

## SHOW TABLES

Displays all tables in current database.

```sql
SHOW TABLES;
```

---

## USE Command

Selects database.

```sql
USE college;
```

---

## DESC Command

Displays table structure.

```sql
DESC student;
```

---

# INSERT Command

## What is INSERT?

Used to add records into a table.

Belongs to DML.

---

## Syntax

```sql
INSERT INTO table_name
VALUES(value1, value2);
```

---

## Example

```sql
INSERT INTO student
VALUES(101, 'Arun', 'CSE');
```

---

## Insert Multiple Rows

```sql
INSERT INTO student
VALUES
(102, 'Neha', 'ECE'),
(103, 'Rahul', 'ME');
```

---

## Important Viva Questions

### What happens if datatype mismatches?

DBMS gives error.

### Which clause specifies selected columns?

Column list after table name.

---

# SELECT Command

## What is SELECT?

Used to retrieve data from table.

---

## Select All Columns

```sql
SELECT * FROM student;
```

---

## Select Specific Columns

```sql
SELECT name, dept
FROM student;
```

---

## WHERE Clause

Filters rows.

```sql
SELECT *
FROM student
WHERE dept='CSE';
```

---

## DISTINCT

Removes duplicates.

```sql
SELECT DISTINCT dept
FROM student;
```

---

## ORDER BY

Sorts records.

```sql
SELECT *
FROM student
ORDER BY marks DESC;
```

---

## LIMIT

Restricts number of rows.

```sql
SELECT *
FROM student
LIMIT 2;
```

---

# Operators

## Arithmetic Operators

|Operator|Purpose|
|---|---|
|+|Addition|
|-|Subtraction|
|*|Multiplication|
|/|Division|
|%|Modulus|

---

## Comparison Operators

|Operator|Meaning|
|---|---|
|=|Equal|
|!=|Not equal|
|>|Greater than|
|<|Less than|
|>=|Greater than or equal|
|<=|Less than or equal|

---

## Logical Operators

|Operator|Meaning|
|---|---|
|AND|Both conditions true|
|OR|Any condition true|
|NOT|Reverse condition|

---

## LIKE Operator

Used for pattern matching.

```sql
SELECT *
FROM student
WHERE name LIKE 'A%';
```

---

## BETWEEN Operator

```sql
SELECT *
FROM student
WHERE marks BETWEEN 70 AND 90;
```

---

## IN Operator

```sql
SELECT *
FROM student
WHERE dept IN ('CSE', 'ECE');
```

---

## NOT IN Operator

```sql
SELECT *
FROM student
WHERE dept NOT IN ('CSE', 'ECE');
```

---

# Aggregate Functions

Aggregate functions perform calculations on multiple rows and return single value.

---

## COUNT()

Counts rows.

```sql
SELECT COUNT(*)
FROM student;
```

---

## SUM()

Adds values.

```sql
SELECT SUM(marks)
FROM student;
```

---

## AVG()

Calculates average.

```sql
SELECT AVG(marks)
FROM student;
```

---

Average Formula:

Average = Sum of values / Number of values

---

## MAX()

Finds highest value.

```sql
SELECT MAX(marks)
FROM student;
```

---

## MIN()

Finds lowest value.

```sql
SELECT MIN(marks)
FROM student;
```

---

# GROUP BY

Groups rows having same values.

---

## Example

```sql
SELECT dept, AVG(marks)
FROM student
GROUP BY dept;
```

---

## Important Point

GROUP BY is mostly used with aggregate functions.

---

# HAVING Clause

HAVING filters grouped data.

---

## Example

```sql
SELECT dept, AVG(marks)
FROM student
GROUP BY dept
HAVING AVG(marks) > 80;
```

---

## Difference Between WHERE and HAVING

|WHERE|HAVING|
|---|---|
|Filters rows|Filters groups|

---

# UPDATE Command

Used to modify existing records.

Belongs to DML.

---

## Syntax

```sql
UPDATE table_name
SET column_name = value
WHERE condition;
```

---

## Example

```sql
UPDATE student
SET marks = 95
WHERE rollno = 101;
```

---

## Important Point

Without WHERE clause, all rows are updated.

---

# DELETE Command

Deletes records from table.

---

## Syntax

```sql
DELETE FROM table_name
WHERE condition;
```

---

## Example

```sql
DELETE FROM student
WHERE rollno = 101;
```

---

## Important Point

DELETE removes rows but table structure remains.

---

# DROP Command

Removes entire table permanently.

---

## Example

```sql
DROP TABLE student;
```

---

## Important Point

Structure + data both deleted.

---

# TRUNCATE Command

Removes all rows quickly.

---

## Example

```sql
TRUNCATE TABLE student;
```

---

## Difference Between DELETE, DROP and TRUNCATE

|DELETE|TRUNCATE|DROP|
|---|---|---|
|Deletes rows|Deletes all rows|Deletes entire table|
|Structure remains|Structure remains|Structure removed|

---

# ALTER Command

Used to modify existing table structure.

Belongs to DDL.

---

## ADD COLUMN

```sql
ALTER TABLE student
ADD age INT;
```

---

## MODIFY COLUMN

```sql
ALTER TABLE student
MODIFY name VARCHAR(50);
```

---

## DROP COLUMN

```sql
ALTER TABLE student
DROP COLUMN age;
```

---

## RENAME COLUMN

```sql
ALTER TABLE student
RENAME COLUMN name TO student_name;
```

---

## RENAME TABLE

```sql
ALTER TABLE student
RENAME TO students;
```

---

# Constraints

Constraints are rules applied on columns.

---

## PRIMARY KEY

Uniquely identifies each row.

```sql
rollno INT PRIMARY KEY
```

---

## FOREIGN KEY

Creates relationship between tables.

```sql
FOREIGN KEY(deptid)
REFERENCES department(deptid)
```

---

## NOT NULL

Prevents NULL values.

```sql
name VARCHAR(30) NOT NULL
```

---

## UNIQUE

Prevents duplicate values.

```sql
email VARCHAR(50) UNIQUE
```

---

## CHECK

Restricts values.

```sql
age INT CHECK(age >= 18)
```

---

## DEFAULT

Assigns default value.

```sql
city VARCHAR(20) DEFAULT 'Palakkad'
```

---

# PRIMARY KEY vs FOREIGN KEY

|PRIMARY KEY|FOREIGN KEY|
|---|---|
|Unique identification|Creates relationship|
|No NULL|NULL allowed|

---

# JOINS

Joins combine data from multiple tables.

---

# INNER JOIN

Returns matching rows.

```sql
SELECT student.name, department.deptname
FROM student
INNER JOIN department
ON student.deptid = department.deptid;
```

---

# LEFT JOIN

Returns all left table rows.

```sql
SELECT student.name, department.deptname
FROM student
LEFT JOIN department
ON student.deptid = department.deptid;
```

---

# RIGHT JOIN

Returns all right table rows.

```sql
SELECT student.name, department.deptname
FROM student
RIGHT JOIN department
ON student.deptid = department.deptid;
```

---

# FULL OUTER JOIN

Not directly supported in MySQL.

Use LEFT JOIN + RIGHT JOIN + UNION.

```sql
SELECT *
FROM student
LEFT JOIN department
ON student.deptid = department.deptid

UNION

SELECT *
FROM student
RIGHT JOIN department
ON student.deptid = department.deptid;
```

---

# SELF JOIN

Table joined with itself.

```sql
SELECT A.empname, B.empname
FROM employee A
JOIN employee B
ON A.manager_id = B.empid;
```

---

# CROSS JOIN

Returns Cartesian product.

```sql
SELECT *
FROM table1
CROSS JOIN table2;
```

---

# UNION

Combines results of multiple SELECT queries.

---

## UNION

Removes duplicates.

```sql
SELECT name FROM cse_students
UNION
SELECT name FROM ece_students;
```

---

## UNION ALL

Keeps duplicates.

```sql
SELECT name FROM cse_students
UNION ALL
SELECT name FROM ece_students;
```

---

# Subqueries

Subquery is a query inside another query.

Inner query executes first.

---

# Single Row Subquery

```sql
SELECT *
FROM student
WHERE marks =
(
    SELECT MAX(marks)
    FROM student
);
```

---

# Multiple Row Subquery

```sql
SELECT name
FROM employee
WHERE deptid IN
(
    SELECT deptid
    FROM department
    WHERE deptname='HR'
);
```

---

# Correlated Subquery

```sql
SELECT name, marks
FROM student s1
WHERE marks >
(
    SELECT AVG(marks)
    FROM student s2
    WHERE s1.dept = s2.dept
);
```

---

# EXISTS

```sql
SELECT name
FROM department d
WHERE EXISTS
(
    SELECT *
    FROM employee e
    WHERE d.deptid = e.deptid
);
```

---

# ANY

```sql
SELECT name
FROM employee
WHERE salary > ANY
(
    SELECT salary
    FROM employee
    WHERE deptid=10
);
```

---

# ALL

```sql
SELECT name
FROM employee
WHERE salary > ALL
(
    SELECT salary
    FROM employee
    WHERE deptid=10
);
```

---

# Views

A view is a virtual table based on SQL query.

---

# Create View

```sql
CREATE VIEW topper AS
SELECT name, marks
FROM student
WHERE marks > 80;
```

---

# Access View

```sql
SELECT *
FROM topper;
```

---

# Drop View

```sql
DROP VIEW topper;
```

---

# Important Differences

## DELETE vs TRUNCATE vs DROP

|DELETE|TRUNCATE|DROP|
|---|---|---|
|Removes rows|Removes all rows|Removes entire table|
|WHERE allowed|WHERE not allowed|Table deleted|
|DML|DDL|DDL|

---

## WHERE vs HAVING

|WHERE|HAVING|
|---|---|
|Filters rows|Filters groups|

---

## UNION vs UNION ALL

|UNION|UNION ALL|
|---|---|
|Removes duplicates|Keeps duplicates|

---

## INNER JOIN vs LEFT JOIN

|INNER JOIN|LEFT JOIN|
|---|---|
|Matching rows only|All left rows|

---

# Most Important Viva Questions 🎤

## What is DBMS?

Software used to manage databases.

---

## Difference between DDL and DML

|DDL|DML|
|---|---|
|Changes structure|Changes data|

---

## Examples of DDL Commands

- CREATE
    
- ALTER
    
- DROP
    
- TRUNCATE
    

---

## Examples of DML Commands

- INSERT
    
- UPDATE
    
- DELETE
    

---

## Which clause filters rows?

WHERE.

---

## Which clause filters groups?

HAVING.

---

## Which join returns matching rows only?

INNER JOIN.

---

## Which operator removes duplicates?

DISTINCT.

---

## Which function counts rows?

COUNT().

---

## Which command modifies existing data?

UPDATE.

---

## Which command removes table permanently?

DROP.

---

## Which command removes all rows quickly?

TRUNCATE.

---

## Which key uniquely identifies rows?

PRIMARY KEY.

---

## Which key creates table relationship?

FOREIGN KEY.

---

# Most Common Teacher Trap Questions 😭

## What happens if WHERE clause is forgotten in UPDATE?

All rows get updated.

---

## What happens if WHERE clause is forgotten in DELETE?

All rows get deleted.

---

## Does TRUNCATE remove structure?

No.

---

## Can PRIMARY KEY contain NULL?

No.

---

## Can UNIQUE contain NULL?

Usually yes.

---

## Does UNION remove duplicates?

Yes.

---

## Does DISTINCT permanently remove duplicates?

No.

---

## Does VIEW store data permanently?

No.

---

## Does MySQL support FULL OUTER JOIN directly?

No.

---

# Final Quick Revision ⚡

|Topic|Key Idea|
|---|---|
|Database|Collection of data|
|DBMS|Manages database|
|CREATE|Create structure|
|INSERT|Add records|
|SELECT|Retrieve data|
|UPDATE|Modify data|
|DELETE|Remove rows|
|DROP|Remove table|
|TRUNCATE|Remove all rows|
|ALTER|Modify structure|
|GROUP BY|Group rows|
|HAVING|Filter groups|
|JOIN|Combine tables|
|UNION|Combine query results|
|VIEW|Virtual table|
|Subquery|Query inside query|

[[DBMS Lab Experiments]]