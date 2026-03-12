# 1️⃣ Aim of the Experiment

To practice **Transaction Control Language (TCL)** and **Data Control Language (DCL)** commands such as:

- **START TRANSACTION**
    
- **SAVEPOINT**
    
- **ROLLBACK**
    
- **COMMIT**
    
- **GRANT**
    
- **REVOKE**
    

These commands help manage **transactions and user access control in databases**.

---

# 2️⃣ Concepts Used

This experiment demonstrates:

|Concept|Purpose|
|---|---|
|Transaction|Logical unit of database operations|
|TCL|Controls transactions|
|DCL|Controls database permissions|
|Savepoints|Partial rollback points|
|User privileges|Security and access control|

---

# 3️⃣ Transaction Control Language (TCL)

TCL commands manage **database transactions**.

Important commands:

|Command|Purpose|
|---|---|
|START TRANSACTION|Begins transaction|
|SAVEPOINT|Creates checkpoint|
|ROLLBACK|Undo changes|
|COMMIT|Save changes permanently|

---

# 4️⃣ SQL Code Explanation

---

# Step 1: Create Database

```
CREATE DATABASE IF NOT EXISTS Exp_7;  
USE Exp_7;
```

Explanation:

`CREATE DATABASE`

Creates database **Exp_7**.

`IF NOT EXISTS`

Prevents error if database already exists.

`USE Exp_7`

Selects database.

---

# Step 2: Create Employees Table

```
CREATE TABLE Employees (  
EmpID INT PRIMARY KEY,  
EmpName VARCHAR(50),  
Salary INT  
);
```

Explanation:

|Column|Purpose|
|---|---|
|EmpID|Unique employee ID|
|EmpName|Employee name|
|Salary|Employee salary|

`PRIMARY KEY`

Ensures:

- Unique employee ID
    
- No duplicate records
    

---

# 5️⃣ START TRANSACTION

```
START TRANSACTION;
```

Explanation:

Begins a **transaction block**.

Changes made after this command are **temporary until COMMIT**.

---

# Insert Records

```
INSERT INTO Employees VALUES (1, 'John', 36000);  
INSERT INTO Employees VALUES (2, 'Asha', 39000);
```

Table becomes:

|EmpID|Name|Salary|
|---|---|---|
|1|John|36000|
|2|Asha|39000|

---

# 6️⃣ SAVEPOINT

```
SAVEPOINT A;
```

Explanation:

Creates **checkpoint A**.

Database can rollback to this point later.

---

# Insert Another Record

```
INSERT INTO Employees VALUES (3, 'Rahul', 42000);
```

Table becomes:

|EmpID|Name|Salary|
|---|---|---|
|1|John|36000|
|2|Asha|39000|
|3|Rahul|42000|

---

# Create Second Savepoint

```
SAVEPOINT B;
```

Checkpoint **B** created.

---

# Insert Another Record

```
INSERT INTO Employees VALUES (4, 'Meena', 45000);
```

Table becomes:

|EmpID|Name|Salary|
|---|---|---|
|1|John||
|2|Asha||
|3|Rahul||
|4|Meena||

---

# 7️⃣ ROLLBACK TO SAVEPOINT

`ROLLBACK TO A;`

Explanation:

Removes all changes **after Savepoint A**.

Records removed:

- Rahul
    
- Meena
    

Table becomes:

|EmpID|Name|
|---|---|
|1|John|
|2|Asha|

---

# 8️⃣ ROLLBACK Entire Transaction

```
ROLLBACK;
```

Explanation:

Undo **all changes since START TRANSACTION**.

Table becomes:

Empty table

Because all inserts were rolled back.

---

# 9️⃣ Data Control Language (DCL)

DCL commands manage **database security and access control**.

Commands used:

|Command|Purpose|
|---|---|
|CREATE USER|Creates new database user|
|GRANT|Gives privileges|
|REVOKE|Removes privileges|
|DROP USER|Deletes user|

---

# Create User

```
CREATE USER 'test'@'localhost' IDENTIFIED BY 'pass123';
```

Explanation:

Creates new user:

Username: test  
Password: pass123  
Host: localhost

---

# Grant Privileges

```
GRANT SELECT, INSERT  
ON Exp_7.Employees  
TO 'test'@'localhost';
```

Explanation:

User **test** can now:

- SELECT data
    
- INSERT data
    

But cannot:

- DELETE
    
- UPDATE
    

---

# Apply Changes

```
FLUSH PRIVILEGES;
```

Explanation:

Reloads privilege tables so changes take effect immediately.

---

# Check Privileges

```
SHOW GRANTS FOR 'test'@'localhost';
```

Displays permissions assigned to user.

---

# Grant All Privileges

```
GRANT ALL PRIVILEGES  
ON Exp_7.Employees  
TO 'test'@'localhost';
```

User now has **full access** to Employees table.

---

# Revoke Privileges

```
REVOKE INSERT  
ON Exp_7.Employees  
FROM 'test'@'localhost';
```

Removes INSERT permission.

---

# Remove All Privileges

```
REVOKE ALL PRIVILEGES, GRANT OPTION  
FROM 'test'@'localhost';
```

Removes every permission.

---

# Delete User

```
DROP USER 'test'@'localhost';
```

Deletes user from database.

---

# 🔟 Result

The TCL and DCL commands were executed successfully to manage transactions and user access privileges in the database.

---

# Possible Viva Questions (With Answers)

---

### Q1. What is a transaction?

**Answer**

A transaction is a sequence of database operations performed as a single logical unit.

---

### Q2. What is TCL?

**Answer**

Transaction Control Language is used to manage transactions in a database.

Examples:

- COMMIT
    
- ROLLBACK
    
- SAVEPOINT
    

---

### Q3. What is COMMIT?

**Answer**

COMMIT permanently saves all changes made during a transaction.

---

### Q4. What is ROLLBACK?

**Answer**

ROLLBACK cancels all changes made during a transaction.

---

### Q5. What is SAVEPOINT?

**Answer**

SAVEPOINT creates a checkpoint within a transaction to which we can rollback later.

---

### Q6. What is DCL?

**Answer**

Data Control Language controls database access and permissions.

---

### Q7. What does GRANT do?

**Answer**

GRANT provides specific privileges to a database user.

---

### Q8. What does REVOKE do?

**Answer**

REVOKE removes privileges from a user.

---

### Q9. What is FLUSH PRIVILEGES?

**Answer**

It reloads privilege tables so that permission changes take effect immediately.

---

### Q10. What is the difference between COMMIT and ROLLBACK?

|COMMIT|ROLLBACK|
|---|---|
|Saves changes permanently|Undoes changes|

---

# Tricky Viva Questions (Teachers Ask These)

---

### Q: Can we rollback after COMMIT?

Answer:

No. Once committed, changes are permanent.

---

### Q: Can SAVEPOINT be used without transaction?

Answer:

No. SAVEPOINT must be inside a transaction.

---

### Q: What happens if ROLLBACK is executed without SAVEPOINT?

Answer:

Entire transaction is undone.

---

### Q: Why are transactions important?

Answer:

They ensure **data consistency and integrity**.