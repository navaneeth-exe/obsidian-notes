
# Complete SQL & CQL Lab Questions, Tables, Answers and Explanations
---

# 1. Supplier Table (SQL)

## Table: Supplier

|Sup_No (Primary Key)|Sup_Name|Item_Supplied|Item_Price|City|
|---|---|---|---|---|
|S1|Suresh|Keyboard|400|Hyderabad|
|S2|Kiran|Processor|8000|Delhi|
|S3|Mohan|Mouse|350|Delhi|
|S4|Ramesh|Processor|9000|Bangalore|
|S5|Manish|Printer|6000|Mumbai|
|S6|Srikanth|Processor|8500|Chennai|

---

## 1. Create Supplier Table

```sql
CREATE TABLE Supplier (
    Sup_No VARCHAR(5) PRIMARY KEY,
    Sup_Name VARCHAR(50),
    Item_Supplied VARCHAR(50),
    Item_Price INT,
    City VARCHAR(50)
);
```

---

## 2. Display supplier numbers and names whose name starts with 'R'

```sql
SELECT Sup_No, Sup_Name
FROM Supplier
WHERE Sup_Name LIKE 'R%';
```

Explanation:

- LIKE is used for pattern matching.
    
- R% means starts with R.
    

---

## 3. Display names of suppliers who supply Processor and whose city is Delhi

```sql
SELECT Sup_Name
FROM Supplier
WHERE Item_Supplied = 'Processor' AND City = 'Delhi';
```

---

## 4. Display names of suppliers who supply the same items as supplied by Ramesh

```sql
SELECT Sup_Name
FROM Supplier
WHERE Item_Supplied = (
    SELECT Item_Supplied
    FROM Supplier
    WHERE Sup_Name = 'Ramesh'
);
```

Explanation:

- Subquery finds the item supplied by Ramesh.
    
- Outer query finds suppliers supplying the same item.
    

---

## 5. Increase the price of Keyboard by 200

```sql
UPDATE Supplier
SET Item_Price = Item_Price + 200
WHERE Item_Supplied = 'Keyboard';
```

---

## 6. Display supplier numbers, names and item price for suppliers in Delhi in ascending order of item price

```sql
SELECT Sup_No, Sup_Name, Item_Price
FROM Supplier
WHERE City = 'Delhi'
ORDER BY Item_Price ASC;
```

---

## 7. Add a new column CONTACTNO

```sql
ALTER TABLE Supplier
ADD CONTACTNO VARCHAR(15);
```

---

# 2. Employee and Department Tables

## Department Table

|DeptId|Dname|
|---|---|
|D1|Sales|
|D2|Marketing|
|D3|Finance|

---

## Employee Table

|Eid|Ename|DeptId|Designation|Salary|DOJ|
|---|---|---|---|---|---|
|101|Sudha|D2|Clerk|20000|01-Apr-10|
|102|David|D1|Manager|50000|18-Feb-18|
|103|Preethi|D3|Clerk|35000|13-Jun-11|
|104|Kiran|D1|Salesman|20000|07-Mar-14|
|105|Meenal|D2|Clerk|50000|09-Dec-11|
|106|Sunitha|D3|Manager|60000|25-Sep-18|
|107|Akhil|D3|Clerk|25000|14-Feb-16|
|108|Sushma|D2|Manager|45000|31-Jan-12|

---

## Create Department Table

```sql
CREATE TABLE Department (
    DeptId VARCHAR(5) PRIMARY KEY,
    Dname VARCHAR(50) NOT NULL
);
```

---

## Create Employee Table

```sql
CREATE TABLE Employee (
    Eid INT PRIMARY KEY,
    Ename VARCHAR(50),
    DeptId VARCHAR(5),
    Designation VARCHAR(50),
    Salary INT CHECK (Salary >= 10000),
    DOJ DATE,
    FOREIGN KEY (DeptId) REFERENCES Department(DeptId)
);
```

---

## 1. Display employees earning more than average salary

```sql
SELECT *
FROM Employee
WHERE Salary > (SELECT AVG(Salary) FROM Employee);
```

---

## 2. Display Eid, Ename and Dname

```sql
SELECT E.Eid, E.Ename, D.Dname
FROM Employee E
JOIN Department D
ON E.DeptId = D.DeptId;
```

---

## 3. Sort employee table in descending order of salaries

```sql
SELECT *
FROM Employee
ORDER BY Salary DESC;
```

---

## 4. List all job designations without repetitions

```sql
SELECT DISTINCT Designation
FROM Employee;
```

---

## 5. Display employee details department-wise and in ascending order of salary

```sql
SELECT *
FROM Employee
ORDER BY DeptId, Salary ASC;
```

---

## 6. Display all clerks in DeptId D2

```sql
SELECT *
FROM Employee
WHERE Designation = 'Clerk' AND DeptId = 'D2';
```

---

## 7. Display employees who joined in the year 2011

```sql
SELECT *
FROM Employee
WHERE YEAR(DOJ) = 2011;
```

---

# 3. EmpDetails Table

## Table: EmpDetails

|Eid|Ename|DOB|Designation|Salary|DOJ|
|---|---|---|---|---|---|
|E101|Suma|29-Dec-89|Designer|20000|01-Apr-10|
|E102|Amit|10-Jan-95|Programmer|25000|18-Feb-18|
|E103|Payal|15-Aug-85|Tester|35000|13-Jun-11|
|E104|Kiran|20-Apr-90|Programmer|40000|07-Mar-14|
|E105|Meenal|29-May-83|DBA|50000|09-Dec-11|
|E106|Sheila|01-May-70|Analyst|60000|25-Sep-18|
|E107|Swamy|13-Jan-85|Programmer|45000|14-Feb-16|
|E108|Sushma|22-Dec-76|DBA|45000|31-Jan-12|

---

## Create Table

```sql
CREATE TABLE EmpDetails (
    Eid VARCHAR(5) PRIMARY KEY,
    Ename VARCHAR(50),
    DOB DATE,
    Designation VARCHAR(50),
    Salary INT,
    DOJ DATE
);
```

---

## 1. Display employees whose designation is Programmer

```sql
SELECT *
FROM EmpDetails
WHERE Designation = 'Programmer';
```

---

## 2. Display employees who joined after 2014

```sql
SELECT *
FROM EmpDetails
WHERE YEAR(DOJ) > 2014;
```

---

## 3. Display employees whose name ends with 'a'

```sql
SELECT *
FROM EmpDetails
WHERE Ename LIKE '%a';
```

---

## 4. Display total salary of employees whose designation is Programmer

```sql
SELECT SUM(Salary)
FROM EmpDetails
WHERE Designation = 'Programmer';
```

---

## 5. Display all employee names in uppercase

```sql
SELECT UPPER(Ename)
FROM EmpDetails;
```

---

## 6. Display details of employee with highest experience

```sql
SELECT *
FROM EmpDetails
WHERE DOJ = (SELECT MIN(DOJ) FROM EmpDetails);
```

---

## 7. Display employees whose name contains 'ee'

```sql
SELECT *
FROM EmpDetails
WHERE Ename LIKE '%ee%';
```

---

# 4. Library Table

## Table: Library

|BookId|BookName|Author|DatePurchased|Publisher|Price|
|---|---|---|---|---|---|
|B101|Cost Accounting|Jain Narang|11-Feb-13|Kalyani|800|
|B102|Business Statistics|OP Aggarwal|22-Dec-11|Himalaya|750|
|B103|RDBMS|C J Date|02-Mar-15|TMH|900|
|B104|Mgmt Accounting|RK Sharma|19-Apr-16|Kalyani|450|
|B105|Operating Systems|Galvin|25-Nov-13|PHI|750|
|B106|Advanced Accounting|SC Gupta|16-Apr-18|Himalaya|600|

---

## Create Table

```sql
CREATE TABLE Library (
    BookId VARCHAR(5) PRIMARY KEY,
    BookName VARCHAR(100) NOT NULL,
    Author VARCHAR(50),
    DatePurchased DATE,
    Publisher VARCHAR(50),
    Price INT
);
```

---

## 1. Display authors from Himalaya publications

```sql
SELECT Author
FROM Library
WHERE Publisher = 'Himalaya';
```

---

## 2. Display total cost of books publisher-wise

```sql
SELECT Publisher, SUM(Price)
FROM Library
GROUP BY Publisher;
```

---

## 3. Count total number of books under Kalyani publications

```sql
SELECT COUNT(*)
FROM Library
WHERE Publisher = 'Kalyani';
```

---

## 4. Rename column Publisher as Publications

```sql
ALTER TABLE Library
RENAME COLUMN Publisher TO Publications;
```

---

## 5. Display books in ascending order of DatePurchased

```sql
SELECT *
FROM Library
ORDER BY DatePurchased ASC;
```

---

## 6. Create index on BookName and Author

```sql
CREATE INDEX idx_book
ON Library (BookName, Author);
```

---

## 7. Display books whose price is between 500 and 700

```sql
SELECT *
FROM Library
WHERE Price BETWEEN 500 AND 700;
```

---

# 5. Student Table

## Table: Student

|Sid|Sname|DOB|State|Gender|Category|Course|
|---|---|---|---|---|---|---|
|1001|Neha|29-Dec-02|Telangana|F|Gen|Comp|
|1002|Arun|10-Jan-02|Telangana|M|OBC|Honors|
|1003|Payal|15-Aug-01|Maharashtra|F|Gen|Appl|
|1004|Amrita|20-Apr-02|Karnataka|F|OBC|Honors|
|1005|Pavan|29-May-03|AndhraPradesh|M|ExServicemen|Comp|
|1006|Anchal|01-May-03|Gujarat|F|OBC|Comp|
|1007|Ramya|13-Jan-02|Telangana|F|Gen|Appl|
|1008|Rakesh|22-Dec-01|AndhraPradesh|M|Sports|Comp|

---

## Create Table

```sql
CREATE TABLE Student (
    Sid INT PRIMARY KEY,
    Sname VARCHAR(50),
    DOB DATE,
    State VARCHAR(50),
    Gender CHAR(1),
    Category VARCHAR(20),
    Course VARCHAR(20)
);
```

---

## 1. Display students not from Telangana or AndhraPradesh

```sql
SELECT *
FROM Student
WHERE State NOT IN ('Telangana','AndhraPradesh');
```

---

## 2. Create a view to display Sid and Sname for Telangana students

```sql
CREATE VIEW Telangana_Students AS
SELECT Sid, Sname
FROM Student
WHERE State = 'Telangana';
```

---

## 3. Create index on Sname

```sql
CREATE INDEX idx_sname
ON Student (Sname);
```

---

## 4. Display female students enrolled under Comp course and belonging to OBC

```sql
SELECT *
FROM Student
WHERE Gender = 'F' AND Course = 'Comp' AND Category = 'OBC';
```

---

## 5. Display student ids, names and present age

```sql
SELECT Sid, Sname, YEAR(CURDATE()) - YEAR(DOB) AS Age
FROM Student;
```

---

## 6. Display students in ascending order of names for each course

```sql
SELECT *
FROM Student
ORDER BY Course, Sname ASC;
```

---

## 7. Delete student records enrolled for Comp course and born after 2002

```sql
DELETE FROM Student
WHERE Course = 'Comp' AND YEAR(DOB) > 2002;
```

---

# 6. Supplier Table (Cassandra CQL)

## Table: Supplier

|Sup_No|Sup_Name|Item_Supplied|Item_Price|City|
|---|---|---|---|---|
|S1|Suresh|Keyboard|400|Hyderabad|
|S2|Kiran|Processor|8000|Delhi|
|S3|Mohan|Mouse|350|Delhi|
|S4|Ramesh|Processor|9000|Bangalore|
|S5|Manish|Printer|6000|Mumbai|
|S6|Srikanth|Processor|8500|Chennai|

---

## 1. Create Supplier table in Cassandra

```sql
CREATE TABLE Supplier (
    Sup_No TEXT PRIMARY KEY,
    Sup_Name TEXT,
    Item_Supplied TEXT,
    Item_Price INT,
    City TEXT
);
```

---

## 2. Insert records into Supplier

```sql
INSERT INTO Supplier VALUES ('S1','Suresh','Keyboard',400,'Hyderabad');
INSERT INTO Supplier VALUES ('S2','Kiran','Processor',8000,'Delhi');
INSERT INTO Supplier VALUES ('S3','Mohan','Mouse',350,'Delhi');
INSERT INTO Supplier VALUES ('S4','Ramesh','Processor',9000,'Bangalore');
INSERT INTO Supplier VALUES ('S5','Manish','Printer',6000,'Mumbai');
INSERT INTO Supplier VALUES ('S6','Srikanth','Processor',8500,'Chennai');
```

---

## 3. Retrieve all records

```sql
SELECT * FROM Supplier;
```

---

## 4. Display suppliers supplying Processor

```sql
SELECT *
FROM Supplier
WHERE Item_Supplied = 'Processor' ALLOW FILTERING;
```

---

## 5. Update Item_Price of S3 from 350 to 400

```sql
UPDATE Supplier
SET Item_Price = 400
WHERE Sup_No = 'S3';
```

---

## 6. Delete supplier S5

```sql
DELETE FROM Supplier
WHERE Sup_No = 'S5';
```

---

## 7. Delete suppliers located in Delhi

```sql
DELETE FROM Supplier
WHERE City = 'Delhi' ALLOW FILTERING;
```

---

# Important SQL Concepts

## ORDER BY

Used to sort records.

```sql
SELECT *
FROM Student
ORDER BY Course, Sname ASC;
```

- First sorts by Course.
    
- Then sorts names within each course.
    

---

## GROUP BY

Used with aggregate functions.

```sql
SELECT Course, COUNT(*)
FROM Student
GROUP BY Course;
```

- Groups rows.
    
- Used with COUNT, SUM, AVG etc.
    

---

## INDEX

Improves query performance and search speed.

```sql
CREATE INDEX idx_sname
ON Student (Sname);
```

- Faster SELECT queries.
    
- Uses extra storage.
    
- Slightly slows INSERT/UPDATE/DELETE.