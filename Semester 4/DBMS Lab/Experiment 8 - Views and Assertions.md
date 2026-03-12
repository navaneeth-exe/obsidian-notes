# 1️⃣ Aim of the Experiment

To practice SQL commands for creating **views and assertions**, and understand how they help enforce **data security and integrity constraints** in a database.

---

# 2️⃣ Concepts Used

This experiment demonstrates:

|Concept|Purpose|
|---|---|
|View|Virtual table based on a query|
|Assertion|Global constraint to enforce rules|
|Check Constraint|Ensures valid data values|

---

# 3️⃣ What is a VIEW?

A **view** is a **virtual table created from a query**.

Important properties:

- Does **not store data physically**
    
- Displays data from **base tables**
    
- Used for **security and simplification**
    

Example:

If the original table has many columns, a view can show **only required columns**.

---

# 4️⃣ SQL Code Explanation

---

# Step 1: Create Database

```
CREATE DATABASE college;  
USE college;
```

Explanation:

- `CREATE DATABASE college` → Creates a database named **college**
    
- `USE college` → Selects the database
    

---

# Step 2: Create Student Table

```
CREATE TABLE student (  
roll_no INT PRIMARY KEY,  
name VARCHAR(50),  
age INT,  
marks INT  
);
```

Explanation:

|Column|Purpose|
|---|---|
|roll_no|Unique student ID|
|name|Student name|
|age|Student age|
|marks|Marks obtained|

`PRIMARY KEY`

Ensures:

- Unique roll number
    
- No duplicate records
    

---

# Step 3: Insert Sample Data

```
INSERT INTO student VALUES  
(1, 'Amit', 19, 75),  
(2, 'Riya', 18, 35),  
(3, 'Karan', 20, 60);
```
Student table becomes:

|roll_no|name|age|marks|
|---|---|---|---|
|1|Amit|19|75|
|2|Riya|18|35|
|3|Karan|20|60|

---

# Step 4: Display Table

```
SELECT * FROM student;
```

Displays all student records.

---

# Step 5: Create View

```
CREATE VIEW passed_students AS  
SELECT roll_no, name, marks  
FROM student  
WHERE marks >= 40;
```

Explanation:

Creates a **view named passed_students**.

This view shows **only students who passed**.

Condition:

marks >= 40

Columns shown:

- roll_no
    
- name
    
- marks
    

---

# Step 6: View Data

```
SELECT * FROM passed_students;
```

Output:

|roll_no|name|marks|
|---|---|---|
|1|Amit|75|
|3|Karan|60|

Student **Riya removed** because marks < 40.

---

# 5️⃣ What is an Assertion?

An **assertion** is a **global constraint** used to enforce conditions across tables.

Example:

```
CREATE ASSERTION valid_marks  
CHECK (  
NOT EXISTS (  
SELECT *  
FROM student  
WHERE marks < 0 OR marks > 100  
)  
);
```

Explanation:

This ensures:

Marks must be between:

0 ≤ marks ≤ 100

If marks are outside this range, insertion will fail.

⚠️ Important:

Most DBMS including **MySQL do not support assertions directly**.

So they are mainly used **for theoretical understanding**.

---

# 6️⃣ Practical Alternative: CHECK Constraint

Instead of assertion, we use **CHECK constraint**.

---

# Create Table with Constraints

```
CREATE TABLE student2 (  
roll_no INT PRIMARY KEY,  
name VARCHAR(50),  
age INT CHECK (age >= 18),  
marks INT CHECK (marks BETWEEN 0 AND 100)  
);
```

Explanation:

Two constraints added:

### Age constraint

age >= 18

Student must be **18 or older**.

---

### Marks constraint

marks BETWEEN 0 AND 100

Marks must be within valid range.

---

# Insert Valid Data

INSERT INTO student2 VALUES  
(1, 'Amit', 19, 75),  
(2, 'Riya', 18, 35),  
(3, 'Karan', 20, 60);

Records inserted successfully.

---

# Insert Invalid Data

INSERT INTO student2 VALUES (4, 'Neha', 19, 150);

Error occurs:

Check constraint violated

Because:

marks = 150 > 100

Constraint prevents invalid data.

---

# Display Data

SELECT * FROM student2;

Table contains only valid records.

|roll_no|name|age|marks|
|---|---|---|---|
|1|Amit|19|75|
|2|Riya|18|35|
|3|Karan|20|60|

Invalid record rejected.

---

# 7️⃣ Result

Views and constraints were successfully implemented to **control data visibility and enforce valid data rules in the database**.

---

# 8️⃣ Possible Viva Questions (With Answers)

---

### Q1. What is a view?

**Answer**

A view is a virtual table created from a SQL query that displays data from one or more base tables.

---

### Q2. Does a view store data?

**Answer**

No. A view does not store data physically; it displays data from base tables.

---

### Q3. Why do we use views?

**Answer**

Views are used to simplify queries, improve security, and provide customized data access.

---

### Q4. What is an assertion?

**Answer**

An assertion is a global constraint that ensures certain conditions remain true in the database.

---

### Q5. Why are assertions rarely used in practice?

**Answer**

Most DBMS systems do not support assertions, so constraints like CHECK are used instead.

---

### Q6. What is a CHECK constraint?

**Answer**

CHECK constraint ensures that column values satisfy a specific condition.

Example:

CHECK (marks BETWEEN 0 AND 100)

---

### Q7. Can views be updated?

**Answer**

Yes, simple views can be updated, but complex views involving joins or aggregates may not be updatable.

---

### Q8. What is the difference between a table and a view?

|Table|View|
|---|---|
|Stores data physically|Virtual table|
|Consumes storage|No storage|
|Contains actual records|Displays query results|

---

### Q9. How can we delete a view?

**Answer**

Using DROP VIEW command.

Example:

DROP VIEW passed_students;

---

### Q10. What is data abstraction?

**Answer**

Data abstraction means hiding complex database details and showing only relevant information to users.

---

# 9️⃣ Tricky Viva Questions

---

### Q: Can we create a view from multiple tables?

Answer:

Yes, views can be created using joins from multiple tables.

---

### Q: What happens if base table data changes?

Answer:

The view automatically shows updated data.

---

### Q: Can a view contain aggregate functions?

Answer:

Yes, but such views may not be updatable.

---

### Q: Can we create a view on another view?

Answer:

Yes.