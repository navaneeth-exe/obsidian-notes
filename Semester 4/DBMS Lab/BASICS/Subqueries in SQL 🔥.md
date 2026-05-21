
A **Subquery** is a query written inside another SQL query.

It is also called:

- Inner Query
    
- Nested Query
    

The inner query executes first, and its result is used by the outer query.

---

# Basic Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name operator
(
    SELECT column_name
    FROM another_table
);
```

---

# Why Subqueries are Used 🧠

Subqueries help when:

- one query depends on another query result
    
- filtering based on calculated values
    
- comparing values from another table
    
- finding maximum/minimum/average etc.
    

---

# Example Table 🎓

## Student Table

|rollno|name|marks|dept|
|---|---|---|---|
|101|Arun|90|CSE|
|102|Neha|85|ECE|
|103|Rahul|70|CSE|
|104|Anu|95|ME|

---

# Types of Subqueries 📚

|Type|Returns|
|---|---|
|Single-row subquery|One value|
|Multiple-row subquery|Multiple values|
|Correlated subquery|Depends on outer query|
|Nested subquery|Query inside query|

---

# 1. Single Row Subquery 🎯

Returns only one value.

Usually used with:

- =
    

- <
    
- > =
    
- <=
    

---

# Example — Students with Highest Marks

```sql
SELECT name, marks
FROM student
WHERE marks =
(
    SELECT MAX(marks)
    FROM student
);
```

---

# Inner Query Executes First

```sql
SELECT MAX(marks)
FROM student;
```

Result:

|MAX(marks)|
|---|
|95|

Then outer query becomes:

```sql
SELECT name, marks
FROM student
WHERE marks = 95;
```

---

# Output

|name|marks|
|---|---|
|Anu|95|

---

# 2. Multiple Row Subquery 🔥

Returns multiple values.

Used with:

- IN
    
- ANY
    
- ALL
    

---

# Example — Students from CSE Department

```sql
SELECT name
FROM student
WHERE dept IN
(
    SELECT dept
    FROM student
    WHERE dept='CSE'
);
```

---

# Another Practical Example

## Employee Table

|empid|name|salary|deptid|
|---|---|---|---|
|1|Arun|50000|10|
|2|Neha|60000|20|
|3|Rahul|45000|10|

---

## Department Table

|deptid|deptname|
|---|---|
|10|HR|
|20|IT|

---

# Query

```sql
SELECT name
FROM employee
WHERE deptid IN
(
    SELECT deptid
    FROM department
    WHERE deptname='HR'
);
```

---

# Output

|name|
|---|
|Arun|
|Rahul|

---

# 3. Correlated Subquery 🔄

A correlated subquery depends on the outer query.

It executes once for every row of outer query.

---

# Example — Students Scoring Above Department Average

```sql
SELECT name, marks, dept
FROM student s1
WHERE marks >
(
    SELECT AVG(marks)
    FROM student s2
    WHERE s1.dept = s2.dept
);
```

---

# How it Works 🧠

For each student:

- DBMS calculates average marks of that student's department
    
- compares individual marks with department average
    

---

# Output Example

|name|marks|dept|
|---|---|---|
|Arun|90|CSE|
|Anu|95|ME|

---

# 4. Nested Subquery 📦

Subquery inside another subquery.

---

# Example

```sql
SELECT name
FROM employee
WHERE deptid =
(
    SELECT deptid
    FROM department
    WHERE managerid =
    (
        SELECT empid
        FROM manager
        WHERE name='Rahul'
    )
);
```

---

# Subquery with Aggregate Functions 📊

---

# Example — Students Above Average Marks

```sql
SELECT name, marks
FROM student
WHERE marks >
(
    SELECT AVG(marks)
    FROM student
);
```

---

# Average Formula

\text{Average} = \frac{\text{Total Marks}}{\text{Number of Students}}

---

# Output

|name|marks|
|---|---|
|Arun|90|
|Anu|95|

---

# Subquery with EXISTS ✅

`EXISTS` checks whether subquery returns rows.

---

# Example

```sql
SELECT name
FROM department d
WHERE EXISTS
(
    SELECT *
    FROM employee e
    WHERE d.deptid = e.deptid
);
```

---

# What it does

Displays departments having employees.

---

# Subquery with NOT EXISTS ❌

```sql
SELECT name
FROM department d
WHERE NOT EXISTS
(
    SELECT *
    FROM employee e
    WHERE d.deptid = e.deptid
);
```

Displays departments without employees.

---

# ANY Operator 🔥

Condition becomes true if it matches any value.

---

# Example

```sql
SELECT name
FROM employee
WHERE salary > ANY
(
    SELECT salary
    FROM employee
    WHERE deptid=10
);
```

---

# ALL Operator ⚡

Condition must satisfy all values.

---

# Example

```sql
SELECT name
FROM employee
WHERE salary > ALL
(
    SELECT salary
    FROM employee
    WHERE deptid=10
);
```

---

# Important Rules 🚨

- Subquery written inside parentheses
    
- Inner query executes first
    
- Subquery can return:
    
    - single value
        
    - multiple rows
        
    - multiple columns
        

---

# Subquery vs Join ⚔️

|Subquery|Join|
|---|---|
|Query inside query|Combines tables|
|Easier for nested conditions|Faster for relationships|

---

# Important Viva Questions 🎤

### Q1. What is a subquery?

A query written inside another query.

---

### Q2. Which query executes first in subquery?

Inner query.

---

### Q3. What is another name for subquery?

Nested query.

---

### Q4. What is correlated subquery?

A subquery dependent on outer query.

---

### Q5. Which operator is commonly used for multiple-row subqueries?

`IN`

---

### Q6. What does EXISTS do?

Checks whether subquery returns rows.

---

### Q7. Difference between ANY and ALL?

|ANY|ALL|
|---|---|
|Condition true for any value|Condition true for all values|

---

### Q8. Can aggregate functions be used in subqueries?

Yes.

---

### Q9. Can subqueries return multiple rows?

Yes.

---

### Q10. Where are subqueries commonly used?

- WHERE
    
- HAVING
    
- FROM
    
- SELECT
    

---

# Common Exam Queries 💀

## Find highest marks

```sql
SELECT *
FROM student
WHERE marks =
(
    SELECT MAX(marks)
    FROM student
);
```

---

## Find students above average marks

```sql
SELECT *
FROM student
WHERE marks >
(
    SELECT AVG(marks)
    FROM student
);
```

---

## Find employees in HR department

```sql
SELECT name
FROM employee
WHERE deptid IN
(
    SELECT deptid
    FROM department
    WHERE deptname='HR'
);
```

---

# Teacher Trap Questions 😭

### “Which query executes first in subquery?”

Inner query.

---

### “Can subquery exist without outer query?”

Yes. Then it becomes normal query 💀

---

### “Which is faster: JOIN or Subquery?”

Usually JOIN.

---

# Quick Revision ⚡

|Type|Description|
|---|---|
|Single-row subquery|Returns one value|
|Multiple-row subquery|Returns many values|
|Correlated subquery|Depends on outer query|
|EXISTS|Checks row existence|
|ANY|Match any value|
|ALL|Match all values|

[[DBMS Lab Experiments]]