
A **View** is a virtual table created from one or more existing tables.

A view does not store data permanently.  
It stores only the SQL query.

Whenever the view is accessed, data is fetched from the original table.

---

# Why Views are Used 🧠

Views are used for:

- security
    
- simplifying complex queries
    
- hiding unnecessary data
    
- presenting customized data
    

---

# Syntax

```sql
CREATE VIEW view_name AS
SELECT column_name
FROM table_name
WHERE condition;
```

---

# Example Table 🎓

## Student Table

|rollno|name|dept|marks|
|---|---|---|---|
|101|Arun|CSE|90|
|102|Neha|ECE|85|
|103|Rahul|CSE|70|

---

# Example 1 — Create Simple View

```sql
CREATE VIEW cse_students AS
SELECT rollno, name, marks
FROM student
WHERE dept='CSE';
```

---

# What it does

Creates a virtual table containing only CSE students.

---

# Accessing the View 🔥

```sql
SELECT *
FROM cse_students;
```

---

# Output

|rollno|name|marks|
|---|---|---|
|101|Arun|90|
|103|Rahul|70|

---

# Important Point 🚨

Original table data is not duplicated.

View only displays filtered/query-based data.

---

# Example 2 — View Using Multiple Tables 🔗

```sql
CREATE VIEW student_dept AS
SELECT student.name, department.deptname
FROM student
JOIN department
ON student.deptid = department.deptid;
```

---

# Advantages of Views ✅

|Advantage|Description|
|---|---|
|Security|Hide sensitive columns|
|Simplicity|Reduce complex queries|
|Reusability|Reuse frequently used queries|
|Data abstraction|User sees only required data|

---

# Updating a View ✏️

Some views are updateable.

---

# Example

```sql
UPDATE cse_students
SET marks = 95
WHERE rollno = 101;
```

This may update original table also.

---

# DROP VIEW ❌

Used to remove a view.

---

# Syntax

```sql
DROP VIEW view_name;
```

---

# Example

```sql
DROP VIEW cse_students;
```

---

# What Happens? 💀

- View deleted
    
- Original table remains safe
    

---

# CREATE OR REPLACE VIEW 🔄

Used to modify existing view.

---

# Example

```sql
CREATE OR REPLACE VIEW cse_students AS
SELECT name, marks
FROM student
WHERE marks > 80;
```

---

# Materialized View ⚡

Some DBMS support materialized views.

Unlike normal views:

- data is stored physically
    
- faster access
    
- needs refresh
    

Examples:

- Oracle Database
    
- PostgreSQL
    

---

# Normal View vs Materialized View ⚔️

|Normal View|Materialized View|
|---|---|
|Stores query only|Stores actual data|
|Slower|Faster|
|Always latest data|Needs refresh|

---

# Important Rules 🚨

- View behaves like table
    
- View does not store actual data
    
- Changes in original table reflect in view
    

---

# Important Viva Questions 🎤

### Q1. What is a view?

A virtual table based on SQL query.

---

### Q2. Does a view store data permanently?

No.

---

### Q3. Why are views used?

For security and simplifying queries.

---

### Q4. Which command creates a view?

`CREATE VIEW`

---

### Q5. Which command removes a view?

`DROP VIEW`

---

### Q6. Can views be created from multiple tables?

Yes.

---

### Q7. What happens if original table changes?

View data also changes.

---

### Q8. Difference between table and view?

|Table|View|
|---|---|
|Stores data|Stores query|

---

### Q9. Can views improve security?

Yes.

---

### Q10. What is materialized view?

A view that stores actual data physically.

---

# Common Exam Queries 💀

## Create view

```sql
CREATE VIEW topper AS
SELECT name, marks
FROM student
WHERE marks > 80;
```

---

## Access view

```sql
SELECT *
FROM topper;
```

---

## Delete view

```sql
DROP VIEW topper;
```

---

# Teacher Trap Questions 😭

### “Does deleting view delete original table?”

No 💀

---

### “Can views contain joins?”

Yes.

---

### “Are views always updateable?”

No. Complex views may not allow updates.

---

# Quick Revision ⚡

|Command|Purpose|
|---|---|
|CREATE VIEW|Create virtual table|
|SELECT|Access view|
|DROP VIEW|Delete view|
|CREATE OR REPLACE VIEW|Modify view|

[[DBMS Lab Experiments]]