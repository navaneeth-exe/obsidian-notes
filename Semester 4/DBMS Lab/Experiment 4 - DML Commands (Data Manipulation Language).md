# 1️⃣ Aim of the Experiment

To perform **data manipulation operations on a database table using SQL commands such as INSERT, SELECT, UPDATE, and DELETE**.

These commands allow users to **retrieve, modify, and remove data stored in tables**.

---

# 2️⃣ Concepts Used

This experiment demonstrates:

- Data Manipulation Language (DML)
    
- Record insertion
    
- Data retrieval
    
- Updating records
    
- Deleting records
    
- Table structure interaction
    

DML commands work on **data inside tables**, unlike DDL which works on **table structure**.

---

# 3️⃣ DML Commands Used

|Command|Purpose|
|---|---|
|SELECT|Retrieve data from table|
|INSERT|Add new records|
|UPDATE|Modify existing records|
|DELETE|Remove records|

---

# 4️⃣ SQL Code Explanation

---

# Step 1: Create Table (DDL)

```
CREATE TABLE students (  
id INT PRIMARY KEY,  
name VARCHAR(100),  
age INT  
);
```

Explanation:

`CREATE TABLE students`

Creates a table named **students**.

Columns:

|Column|Meaning|
|---|---|
|id|Student ID|
|name|Student name|
|age|Student age|

`PRIMARY KEY`

Ensures:

- Each student has a **unique ID**
    
- Cannot contain NULL values
    

⚠️ Note:  
Your insert queries use **grade**, but the table definition doesn't include it. Normally it should be:

```
CREATE TABLE students (  
id INT PRIMARY KEY,  
name VARCHAR(100),  
age INT,  
grade VARCHAR(5)  
);
```

---

# Step 2: INSERT Command

```
INSERT INTO students (id, name, age, grade)  
VALUES (1, 'Rahul', 20, 'A');
```
Explanation:

- `INSERT INTO` → adds a new row
    
- `(id,name,age,grade)` → columns receiving values
    
- `VALUES` → actual data inserted
    

Record inserted:

|id|name|age|grade|
|---|---|---|---|
|1|Rahul|20|A|

---

Another insert:

```
INSERT INTO students (id, name, age, grade)  
VALUES (2, 'Anu', 21, 'B');
```

---

Another insert:

```
INSERT INTO students (id, name, age, grade)  
VALUES (3, 'Neha', 22, 'A');
```
Now table contains:

|id|name|age|grade|
|---|---|---|---|
|1|Rahul|20|A|
|2|Anu|21|B|
|3|Neha|22|A|

---

# Step 3: SELECT Command

```
SELECT * FROM students;
```

Explanation:

`SELECT` retrieves records.

`*` means **all columns**.

Output:

|id|name|age|grade|
|---|---|---|---|
|1|Rahul|20|A|
|2|Anu|21|B|
|3|Neha|22|A|

---

# Step 4: UPDATE Command

```
UPDATE students  
SET grade = 'A+'  
WHERE name = 'Anu';
```

Explanation:

`UPDATE students`

Specifies table to update.

`SET grade = 'A+'`

Changes grade.

`WHERE name = 'Anu'`

Condition ensures only Anu’s record is updated.

After update:

|id|name|age|grade|
|---|---|---|---|
|1|Rahul|20|A|
|2|Anu|21|A+|
|3|Neha|22|A|

---

# Step 5: DELETE Command

```
DELETE FROM students  
WHERE id = 3;
```

Explanation:

`DELETE FROM students`

Deletes records.

`WHERE id = 3`

Deletes only record with ID = 3.

After deletion:

|id|name|age|grade|
|---|---|---|---|
|1|Rahul|20|A|
|2|Anu|21|A+|

Record of **Neha is removed**.

---

# 5️⃣ Result

The DML commands were successfully executed to **insert, retrieve, update, and delete records from the students table**.

---

# 6️⃣ Possible Viva Questions (With Answers)

---

### Q1. What is DML?

**Answer**

DML (Data Manipulation Language) is used to manipulate data stored in database tables.

Examples:

- INSERT
    
- SELECT
    
- UPDATE
    
- DELETE
    

---

### Q2. What is SELECT command?

**Answer**

SELECT is used to retrieve data from one or more tables.

Example:

```
SELECT * FROM students;
```

---

### Q3. What is INSERT command?

**Answer**

INSERT command adds new records to a table.

Example:

```
INSERT INTO students VALUES(1,'Rahul',20,'A');
```

---

### Q4. What is UPDATE command?

**Answer**

UPDATE modifies existing records in a table.

Example:

```
UPDATE students SET grade='A+' WHERE name='Anu';
```

---

### Q5. What is DELETE command?

**Answer**

DELETE removes records from a table based on a condition.

Example:

DELETE FROM students WHERE id=3;

---

### Q6. Why is WHERE clause important?

**Answer**

WHERE clause specifies which records should be affected by UPDATE or DELETE operations.

Without WHERE, all rows will be affected.

---

### Q7. What does * mean in SELECT?

**Answer**

`*` means all columns in the table.

---

### Q8. Can we insert multiple rows?

**Answer**

Yes.

Example:

```
INSERT INTO students VALUES  
(4,'Arya',21,'A'),  
(5,'Kiran',22,'B');
```

---

### Q9. What happens if WHERE clause is omitted in DELETE?

**Answer**

All rows in the table will be deleted.

Example:

```
DELETE FROM students;
```

---

### Q10. What is the difference between DELETE and DROP?

**Answer**

DELETE removes rows from a table, while DROP removes the entire table structure and data.

---

# 7️⃣ Tricky Viva Questions

---

### Q: Which is faster, DELETE or TRUNCATE?

Answer:

TRUNCATE is faster because it removes all rows instantly.

---

### Q: Can DELETE be rolled back?

Answer:

Yes, DELETE can be rolled back if transactions are used.

---

### Q: Can UPDATE change multiple rows?

Answer:

Yes, if the WHERE condition matches multiple rows.