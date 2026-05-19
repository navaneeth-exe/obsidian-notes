

Table creation means creating a new table in a database using the `CREATE TABLE` command.

A table stores data in:

- Rows → records
    
- Columns → attributes
    

---

# Basic Syntax

```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype
);
```

---

# Example 1 — Student Table 🎓

```sql
CREATE TABLE Student (
    rollno INT,
    name VARCHAR(30),
    dept VARCHAR(10)
);
```

---

# What this does

Creates a table named `Student`.

|Column|Datatype|Meaning|
|---|---|---|
|rollno|INT|Integer values|
|name|VARCHAR(30)|Variable-length text|
|dept|VARCHAR(10)|Department name|

---

# Resulting Empty Table

|rollno|name|dept|
|---|---|---|
|Empty initially|||

---

# Example 2 — Employee Table 👨‍💼

```sql
CREATE TABLE Employee (
    empid INT,
    empname VARCHAR(50),
    salary INT
);
```

---

# Common Datatypes 📚

|Datatype|Meaning|
|---|---|
|INT|Integer numbers|
|VARCHAR(n)|Variable text|
|CHAR(n)|Fixed text|
|FLOAT|Decimal numbers|
|DATE|Date values|

---

# Table with Constraints 🔒

```sql
CREATE TABLE Student (
    rollno INT PRIMARY KEY,
    name VARCHAR(30) NOT NULL,
    age INT
);
```

---

# What these constraints do

|Constraint|Purpose|
|---|---|
|PRIMARY KEY|Unique identifier|
|NOT NULL|Cannot store empty value|

---

# Important Terms 🧠

## Row / Tuple

Single record in table.

Example:

|rollno|name|
|---|---|
|101|Arun|

This entire row = tuple.

---

## Column / Attribute

Property of table.

Example:

- rollno
    
- name
    
- dept
    

---

# Possible Viva Questions 🎤

## Q1. What is a table in DBMS?

A collection of related data arranged in rows and columns.

---

## Q2. Which command is used to create a table?

`CREATE TABLE`

---

## Q3. What is the syntax for table creation?

```sql
CREATE TABLE table_name (
    column datatype
);
```

---

## Q4. What is VARCHAR?

Stores variable-length character strings.

Example:  
`VARCHAR(20)`

---

## Q5. Difference between CHAR and VARCHAR?

|CHAR|VARCHAR|
|---|---|
|Fixed size|Variable size|

---

## Q6. What is a primary key?

A column that uniquely identifies each row.

---

## Q7. Can a table exist without records?

Yes. Empty tables can exist.

---

## Q8. What is the difference between row and column?

|Row|Column|
|---|---|
|Record|Attribute|

---

## Q9. What happens if datatype is wrong?

DBMS may show an error or reject data.

---

## Q10. Which command changes table structure later?

`ALTER`

---

# Super Common Exam Program 💀

```sql
CREATE TABLE Book (
    bookid INT PRIMARY KEY,
    title VARCHAR(50),
    author VARCHAR(30),
    price FLOAT
);
```

---

# Teacher Trap Questions 😭

### “Can two primary keys exist in one table?”

Only one PRIMARY KEY constraint, but it can contain multiple columns (composite key).

---

### “Can PRIMARY KEY contain NULL?”

No.

---

### “Can VARCHAR store numbers?”

Yes, but as text.

---

# Quick Revision ⚡

|Command|Purpose|
|---|---|
|CREATE TABLE|Creates new table|
|ALTER TABLE|Modifies table|
|DROP TABLE|Deletes table|