# PRIMARY KEY 🔑

A **Primary Key** is a column (or set of columns) that uniquely identifies each row in a table.

---

# Important Features

- Cannot contain duplicate values
    
- Cannot contain NULL values
    
- Each table usually has one primary key
    

---

# Example

## Student Table

|rollno|name|dept|
|---|---|---|
|101|Arun|CSE|
|102|Neha|ECE|

Here, `rollno` is unique for every student.

So `rollno` = PRIMARY KEY ✅

---

# Syntax

```sql
CREATE TABLE Student (
    rollno INT PRIMARY KEY,
    name VARCHAR(30),
    dept VARCHAR(10)
);
```

---

# What it does

- Makes `rollno` unique
    
- Prevents duplicate/null values
    

---

# Duplicate Example ❌

```sql
INSERT INTO Student
VALUES (101, 'Rahul', 'ME');
```

If `101` already exists → ERROR 💀

---

# FOREIGN KEY 🔗

A **Foreign Key** is a column that creates a relationship between two tables.

It refers to the PRIMARY KEY of another table.

---

# Example

## Department Table

|deptid|deptname|
|---|---|
|1|CSE|
|2|ECE|

`deptid` is PRIMARY KEY.

---

## Student Table

|rollno|name|deptid|
|---|---|---|
|101|Arun|1|
|102|Neha|2|

Here:  
`deptid` in Student table = FOREIGN KEY 🔗

Because it references Department table.

---

# Syntax

```sql
CREATE TABLE Department (
    deptid INT PRIMARY KEY,
    deptname VARCHAR(20)
);

CREATE TABLE Student (
    rollno INT PRIMARY KEY,
    name VARCHAR(30),
    deptid INT,
    FOREIGN KEY (deptid)
    REFERENCES Department(deptid)
);
```

---

# What it does

- Connects tables
    
- Maintains data consistency
    
- Prevents invalid references
    

---

# Real-Life Example 🧠

|Table|Primary Key|
|---|---|
|Student|rollno|
|Department|deptid|

Student table stores `deptid` as FOREIGN KEY to know which department student belongs to.

---

# PRIMARY KEY vs FOREIGN KEY ⚔️

|PRIMARY KEY|FOREIGN KEY|
|---|---|
|Uniquely identifies rows|Links two tables|
|Cannot be NULL|Can contain NULL|
|Only one per table|Multiple allowed|
|Unique values only|Duplicate values allowed|

---

# Important Viva Questions 🎤

### Q1. What is Primary Key?

A key used to uniquely identify each record.

---

### Q2. Can PRIMARY KEY contain NULL?

No.

---

### Q3. Can PRIMARY KEY contain duplicate values?

No.

---

### Q4. What is Foreign Key?

A key used to establish relationship between tables.

---

### Q5. FOREIGN KEY references which key?

PRIMARY KEY.

---

### Q6. Can FOREIGN KEY contain duplicate values?

Yes.

---

### Q7. Why are foreign keys used?

To maintain referential integrity.

---

### Q8. Difference between PRIMARY KEY and FOREIGN KEY?

|PRIMARY KEY|FOREIGN KEY|
|---|---|
|Identifies record|References another table|

---

### Q9. Can a table have multiple foreign keys?

Yes.

---

### Q10. Can a table have more than one primary key?

Only one PRIMARY KEY constraint.

---

# Most Common Exam Example 💀

```sql
CREATE TABLE Customer (
    cid INT PRIMARY KEY,
    cname VARCHAR(30)
);

CREATE TABLE Orders (
    orderid INT PRIMARY KEY,
    cid INT,
    FOREIGN KEY (cid)
    REFERENCES Customer(cid)
);
```

---

# Teacher Trap Questions 😭

### “Can FOREIGN KEY exist without PRIMARY KEY?”

No. It must reference a PRIMARY KEY (or UNIQUE key).

---

### “Can FOREIGN KEY be NULL?”

Yes.

---

### “Why PRIMARY KEY is important?”

Because every row must be uniquely identifiable.

---

# Quick Revision ⚡

|Key|Purpose|
|---|---|
|PRIMARY KEY|Unique identification|
|FOREIGN KEY|Table relationship|



[[DBMS Lab Experiments]]