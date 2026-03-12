# 1️⃣ Aim of the Experiment

To **initialize a database by inserting records into tables** and to perform **bulk export and import of data using SQL commands and UI tools**.

This experiment demonstrates how data is **stored, exported to files, and imported back into the database**.

---

# 2️⃣ Concepts Used in This Experiment

Main DBMS concepts involved:

- Database creation
    
- Table creation
    
- Data insertion
    
- Foreign keys
    
- Primary keys
    
- Check constraints
    
- Bulk export
    
- Bulk import
    
- Data migration
    

---

# 3️⃣ Database Schema Overview

Tables created in this experiment:

|Table|Purpose|
|---|---|
|emp|Stores employee details|
|company|Stores company details|
|works|Shows which employee works for which company|
|manages|Shows manager-employee relationships|

---

# 4️⃣ SQL Code Explanation

---

# Step 1: Create Database

```
CREATE DATABASE test;  
USE test;
```

Explanation:

- `CREATE DATABASE test` → Creates a database named **test**
    
- `USE test` → Selects that database for further operations
    

---

# Step 2: Create Employee Table

```
CREATE TABLE emp (  
emp_id CHAR(8) CHECK(emp_id LIKE 'E%') PRIMARY KEY,  
emp_name VARCHAR(18),  
street_no INT,  
city VARCHAR(18)  
);
```

Explanation:

**emp_id CHAR(8)**  
Stores employee ID.

Example:  
`E-101`

**CHECK(emp_id LIKE 'E%')**

Constraint ensures:

Employee ID **must start with letter E**.

Example valid values:

```
E-101  
E-102
```

Invalid:

```
101  
A-101
```

**PRIMARY KEY**

Ensures:

- Unique employee ID
    
- Cannot be NULL
    

Other attributes:

|Column|Meaning|
|---|---|
|emp_name|Employee name|
|street_no|Street number|
|city|Employee city|

---

# Step 3: Create Company Table

```
CREATE TABLE company (  
company_name VARCHAR(18) PRIMARY KEY,  
city VARCHAR(18)  
);
```

Explanation:

`company_name` is the **primary key**.

This ensures:

- Each company name must be unique.
    

Example data:

|company_name|city|
|---|---|
|SBI|MG Road|
|SBT|MG Road|

---

# Step 4: Create Works Table

```
CREATE TABLE works (  
emp_id CHAR(8) REFERENCES emp(emp_id),  
company_name VARCHAR(18) REFERENCES company(company_name),  
salary FLOAT,  
PRIMARY KEY(emp_id, company_name)  
);
```

Purpose:

Shows **which employee works in which company**.

Explanation:

`emp_id REFERENCES emp(emp_id)`

Foreign key referencing employee table.

`company_name REFERENCES company(company_name)`

Foreign key referencing company table.

`PRIMARY KEY(emp_id, company_name)`

Composite key ensures:

One employee cannot be linked to the **same company twice**.

---

# Step 5: Create Manages Table

```
CREATE TABLE manages (  
emp_id CHAR(8) REFERENCES emp(emp_id),  
manager_id CHAR(8) REFERENCES emp(emp_id),  
UNIQUE(emp_id, manager_id)  
);
```

Purpose:

Stores **manager–employee relationships**.

Explanation:

Both columns reference the **same emp table**.

Example:

|emp_id|manager_id|
|---|---|
|E-101|E-102|

Meaning:

Employee **E-102 manages E-101**.

This is called **self-referencing relationship**.

---

# 5️⃣ Data Insertion

Example:

```
INSERT INTO company VALUES('SBI', 'MG Road');
```

Explanation:

- Inserts a row into company table.
    

Example result:

|company_name|city|
|---|---|
|SBI|MG Road|

---

Another example:

```
INSERT INTO emp VALUES('E-101','Adarsh',101,'MG Road');
```

Explanation:

- Adds employee Adarsh with ID E-101.
    

---

Example for works table:

```
INSERT INTO works VALUES('E-101','SBI',71000);
```

Meaning:

Employee **E-101 works in SBI with salary 71000**.

---

Example for manages table:

```
INSERT INTO manages VALUES('E-101','E-102');
```

Meaning:

Employee **E-102 is manager of E-101**.

---

# 6️⃣ Export Data to Text File

First check export location:

```
SHOW VARIABLES LIKE 'secure_file_priv';
```

Explanation:

This command shows the **allowed folder for file export/import**.

Example output:

```
/var/lib/mysql-files/
```
MySQL only allows file operations inside this directory for security.

---

# Export Query

```
SELECT * FROM works INTO OUTFILE "/var/lib/mysql-files/out2.txt";
```

Explanation:

This command exports **all records from works table into a text file**.

File created:

out2.txt

Contents example:

E-101 SBI 71000  
E-102 SBI 90000  
E-103 SBT 40000

---

# View File Content

Using Linux command:

```
cat /var/lib/mysql-files/out2.txt
```

Displays contents of exported file.

---

# 7️⃣ Import Data from Text File

Create new table:

```
CREATE TABLE working(  
emp_id CHAR(8) REFERENCES emp(emp_id),  
company_name VARCHAR(18) REFERENCES company(company_name),  
salary FLOAT,  
PRIMARY KEY(emp_id, company_name)  
);

```
---

# Import Query

```
LOAD DATA INFILE "/var/lib/mysql-files/out2.txt"  
INTO TABLE test.working;
```
Explanation:

- Loads data from text file
    
- Inserts records into table **working**
    

This is called **bulk import**.

---

# 8️⃣ Verify Imported Data

```
SELECT * FROM working;
```

Shows the imported rows.

Example output:

|emp_id|company|salary|
|---|---|---|
|E-101|SBI|71000|
|E-102|SBI|90000|

---

# 9️⃣ Possible Viva Questions (With Answers)

---

### Q1. What is database initialization?

**Answer**

Database initialization is the process of inserting initial data into tables after the database structure is created.

---

### Q2. What is the INSERT command?

**Answer**

INSERT command is used to add new records into a table.

Example:

INSERT INTO emp VALUES('E-101','Adarsh',101,'MG Road');

---

### Q3. What is bulk import?

**Answer**

Bulk import is the process of inserting large amounts of data into a database from external files such as CSV or text files.

---

### Q4. What is bulk export?

**Answer**

Bulk export is the process of transferring database data into external files.

---

### Q5. What is the purpose of LOAD DATA INFILE?

**Answer**

LOAD DATA INFILE is used to import large datasets from a file into a database table efficiently.

---

### Q6. What is a CHECK constraint?

**Answer**

A CHECK constraint ensures that column values satisfy a specific condition.

Example:

CHECK(emp_id LIKE 'E%')

Ensures employee IDs start with E.

---

### Q7. What is a composite primary key?

**Answer**

A composite primary key consists of **multiple columns used together to uniquely identify a record**.

Example:

PRIMARY KEY(emp_id, company_name)

---

### Q8. What is a self-referencing foreign key?

**Answer**

A foreign key that references the same table.

Example:

Manager referencing employee table.

---

### Q9. Why do we use SELECT INTO OUTFILE?

**Answer**

To export table data into external files.

---

### Q10. What is secure_file_priv?

**Answer**

secure_file_priv defines the directory where MySQL allows file import/export operations.

---

# 🔟 Tricky Viva Questions (Teachers Love These)

---

### Q: Can an employee have multiple managers?

Answer:

No, because **UNIQUE(emp_id, manager_id)** restricts duplicate manager relationships.

---

### Q: Why use composite primary key in works table?

Answer:

To prevent duplicate records for the same employee and company.

---

### Q: Why is CHECK constraint used?

Answer:

To ensure valid data entry.

Example:

Employee ID must start with **E**