# 1. Database 📦

A **Database** is an organized collection of related data stored electronically.

### Example

Student database in a college:

|Roll No|Name|Dept|
|---|---|---|
|101|Arun|CSE|
|102|Neha|ECE|

Here, all student records together form a database.

### Real-life Examples

- Banking system
    
- Instagram user data
    
- College management system
    
- Hospital records
    

### What it does

- Stores data permanently
    
- Makes searching easy
    
- Reduces data redundancy
    
- Helps multiple users access data
    

---

# 2. DBMS 🧠

A **DBMS (Database Management System)** is software used to create, manage, and manipulate databases.

Examples:

- MySQL
    
- Oracle Database
    
- MongoDB
    
- PostgreSQL
    

---

## What DBMS does

- Creates databases
    
- Stores and retrieves data
    
- Provides security
    
- Controls access
    
- Performs backup and recovery
    

---

## Advantages of DBMS

- Reduced redundancy
    
- Better security
    
- Data consistency
    
- Multi-user access
    
- Faster data retrieval
    

---

# Possible Viva Questions for Database & DBMS 🎤

## Basic Viva

### Q1. What is a database?

A database is an organized collection of related data.

### Q2. What is DBMS?

DBMS is software used to manage databases.

### Q3. Difference between database and DBMS?

|Database|DBMS|
|---|---|
|Collection of data|Software to manage data|

---

### Q4. Give examples of DBMS.

- MySQL
    
- Oracle
    
- PostgreSQL
    
- MongoDB
    

---

### Q5. What are the advantages of DBMS?

- Security
    
- Reduced redundancy
    
- Easy data access
    
- Backup and recovery
    

---

### Q6. What is data redundancy?

Duplicate data stored in multiple places.

---

### Q7. What is data inconsistency?

When same data has different values in different places.

Example:  
One table says age = 20  
Another says age = 22 💀

---

# 3. CREATE Command 🏗️

`CREATE` is a DDL (Data Definition Language) command used to create databases, tables, views, etc.

---

## Syntax

```sql
CREATE TABLE student (
    rollno INT,
    name VARCHAR(20),
    dept VARCHAR(10)
);
```

---

## Example

```sql
CREATE TABLE Employee (
    empid INT,
    name VARCHAR(30),
    salary INT
);
```

---

## What it does

Creates a new table named `Employee`.

---

## Output Structure

|empid|name|salary|
|---|---|---|
|Empty table created|||

---

# Viva Questions for CREATE 🎤

### Q1. What is CREATE command?

Used to create database objects like tables.

---

### Q2. Which category does CREATE belong to?

DDL (Data Definition Language)

---

### Q3. Can CREATE create a database?

Yes.

Example:

```sql
CREATE DATABASE College;
```

---

### Q4. What happens if table already exists?

DBMS shows an error.

---

### Q5. Difference between CREATE and INSERT?

|CREATE|INSERT|
|---|---|
|Creates structure|Adds records|

---

# 4. ALTER Command 🔧

`ALTER` is used to modify the structure of an existing table.

You can:

- Add column
    
- Delete column
    
- Modify datatype
    
- Rename column
    

---

# ALTER Examples

---

## 1. Add Column

```sql
ALTER TABLE student
ADD age INT;
```

### What it does

Adds a new column `age`.

---

## 2. Modify Column

```sql
ALTER TABLE student
MODIFY name VARCHAR(50);
```

### What it does

Changes size of `name` column.

---

## 3. Drop Column

```sql
ALTER TABLE student
DROP COLUMN age;
```

### What it does

Deletes `age` column.

---

## 4. Rename Column

```sql
ALTER TABLE student
RENAME COLUMN name TO student_name;
```

---

# Viva Questions for ALTER 🎤

### Q1. What is ALTER command?

Used to modify existing table structure.

---

### Q2. Which language category does ALTER belong to?

DDL.

---

### Q3. Can ALTER add columns?

Yes.

---

### Q4. Can ALTER delete columns?

Yes.

---

### Q5. Difference between ALTER and UPDATE?

|ALTER|UPDATE|
|---|---|
|Changes table structure|Changes data|

---

### Q6. Which command removes a column?

`DROP COLUMN`

---

# Super Important Exam Point 🚨

## DDL Commands

These change database structure.

- CREATE
    
- ALTER
    
- DROP
    
- TRUNCATE
    

---

## DML Commands

These manipulate data.

- INSERT
    
- UPDATE
    
- DELETE
    

---

# One-Line Definitions for Fast Revision ⚡

|Term|Definition|
|---|---|
|Database|Organized collection of data|
|DBMS|Software to manage database|
|CREATE|Creates database objects|
|ALTER|Modifies existing table|

---

# Very Common Teacher Trap Questions 😭

### “Can ALTER recover deleted columns?”

Usually no, unless backup exists.

---

### “Is CREATE used to insert records?”

No. INSERT is used.

---

### “Does ALTER affect data?”

Mostly structure changes, but some operations can affect data.

---

### “Why is DBMS better than file system?”

- Better security
    
- Less redundancy
    
- Faster access
    
- Multi-user support