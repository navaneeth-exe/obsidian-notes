# 1️⃣ Aim of the Experiment

To **create, modify, and delete database structures using SQL DDL commands**, and understand how database schemas are managed.

DDL commands allow us to **define the structure of a database** such as tables, attributes, and constraints.

---

# 2️⃣ Concepts Used in This Experiment

This experiment demonstrates:

- **DDL (Data Definition Language)**
    
- **Database creation**
    
- **Table creation**
    
- **Schema modification**
    
- **Table deletion**
    
- **Database deletion**
    
- **Table renaming**
    
- **Data removal using TRUNCATE**
    

DDL commands affect **database structure**, not just the data.

---

# 3️⃣ DDL Commands Used

|Command|Purpose|
|---|---|
|CREATE|Create database objects|
|ALTER|Modify table structure|
|DROP|Delete database objects|
|TRUNCATE|Remove all records quickly|
|RENAME|Change object name|
|COMMENT|Add descriptions|

---

# 4️⃣ Code / Query Explanation

---

# Step 1: Create Database

```
create database testdb;
```

Explanation:

- `create database` → SQL command to create a new database
    
- `testdb` → Name of the database
    

Result:  
A new database called **testdb** is created.

---

# Step 2: Select the Database

```
use testdb;
```

Explanation:

- `use` → Selects the database to work with
    
- `testdb` → Database name
    

After this command, all tables will be created inside **testdb**.

---

# Step 3: Create Table

```
create table student (  
stname varchar(30),  
stid varchar(10),  
stage int(2),  
starea varchar(20)  
);
```

Explanation:

`CREATE TABLE student`

Creates a table named **student**.

Columns:

|Column|Datatype|Purpose|
|---|---|---|
|stname|varchar(30)|Student name|
|stid|varchar(10)|Student ID|
|stage|int(2)|Student age|
|starea|varchar(20)|Student area/location|

Datatype explanation:

- **VARCHAR(n)** → variable-length string
    
- **INT(n)** → integer number
    

---

# Step 4: Describe Table Structure

```
desc student;
```

Explanation:

- `desc` means **describe**
    
- Displays table structure
    

Output shows:

- Column names
    
- Datatypes
    
- Null constraints
    
- Keys
    

Example output:

|Field|Type|Null|Key|
|---|---|---|---|
|stname|varchar(30)|YES||
|stid|varchar(10)|YES||
|stage|int(2)|YES||
|starea|varchar(20)|YES||

---

# Step 5: Modify Table Column

`alter table student modify stage int(5);`

Explanation:

`ALTER TABLE` → used to change table structure.

`modify stage int(5)`

Changes the datatype of column **stage** to allow **larger numbers**.

Before:

stage INT(2)

After:

stage INT(5)

---

# Step 6: Drop Column

```
alter table student drop stdept;
```

Explanation:

- `drop` removes a column permanently
    
- `stdept` column is removed from table
    

⚠️ Note:  
If column doesn't exist, it will give an error.

---

# Step 7: Clear Table Data

```
truncate table student;
```

Explanation:

- `truncate` removes **all records from the table**
    
- Table structure remains the same
    

Difference from DELETE:

|DELETE|TRUNCATE|
|---|---|
|Deletes rows one by one|Deletes all rows instantly|
|Can use WHERE|No WHERE clause|
|Slower|Faster|

---

# Step 8: Rename Table

```
ALTER TABLE student RENAME TO students;
```

Explanation:

Changes table name:

student → students

---

# Step 9: Delete Table

```
drop table student;
```

Explanation:

- `DROP TABLE` removes the **entire table**
    
- Deletes both **data and structure**
    

After dropping, table no longer exists.

Example error after drop:

```
ERROR 1146: Table doesn't exist
```

---

# Step 10: Delete Database

```
DROP DATABASE databasename;
```

Explanation:

- Deletes the **entire database**
    
- Removes all tables and data permanently.
    

Example:

DROP DATABASE testdb;

---

# 6️⃣ Possible Viva Questions (With Answers)

---

### Q1. What is DDL?

**Answer**

DDL (Data Definition Language) is used to define and modify the structure of database objects such as tables, schemas, and indexes.

---

### Q2. Name some DDL commands.

**Answer**

Common DDL commands:

- CREATE
    
- ALTER
    
- DROP
    
- TRUNCATE
    
- RENAME
    

---

### Q3. What does CREATE command do?

**Answer**

CREATE command is used to create database objects such as tables, databases, indexes, and views.

---

### Q4. What is ALTER command?

**Answer**

ALTER command is used to modify the structure of an existing table, such as adding, deleting, or modifying columns.

---

### Q5. What does TRUNCATE do?

**Answer**

TRUNCATE removes all rows from a table but keeps the table structure.

---

### Q6. Difference between DELETE and TRUNCATE?

**Answer**

DELETE removes rows using conditions and can be rolled back, while TRUNCATE removes all rows instantly and cannot be rolled back.

---

### Q7. What is DROP command?

**Answer**

DROP command permanently deletes a database object such as a table or database along with its data.

---

### Q8. What does DESC command do?

**Answer**

DESC displays the structure of a table including column names, datatypes, and constraints.

---

### Q9. What is schema?

**Answer**

A schema is the logical structure of a database including tables, attributes, and relationships.

---

### Q10. What happens when a table is dropped?

**Answer**

Both the table structure and all stored data are permanently deleted.

---

# 7️⃣ Tricky Viva Questions (Very Likely)

---

### Q: Which is faster, DELETE or TRUNCATE?

Answer:

TRUNCATE is faster because it removes all records at once instead of deleting rows individually.

---

### Q: Can TRUNCATE be rolled back?

Answer:

Usually **No**, because it is a DDL operation.

---

### Q: Can we recover a dropped table?

Answer:

No, once a table is dropped it is permanently deleted unless backup exists.

---

### Q: What is the difference between schema and database?

Answer:

- **Database** → collection of data
    
- **Schema** → structure or blueprint of the database