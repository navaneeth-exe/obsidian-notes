
Joins are used to combine data from two or more tables based on a related column.

They help retrieve related information stored in different tables.

Without joins, relational databases would basically be useless 😭

---

# Why JOINS are Needed 🧠

In DBMS, data is usually stored in multiple tables to:

- reduce redundancy
    
- improve organization
    
- maintain relationships
    

Joins help connect these tables.

---

# Example Tables 🎓

## Student Table

|sid|name|deptid|
|---|---|---|
|1|Arun|101|
|2|Neha|102|
|3|Rahul|101|

---

## Department Table

|deptid|deptname|
|---|---|
|101|CSE|
|102|ECE|
|103|ME|

---

Here:

- `deptid` is PRIMARY KEY in Department table
    
- `deptid` is FOREIGN KEY in Student table
    

This relationship is used for joins.

---

# Types of JOINS 📚

|Join|Purpose|
|---|---|
|INNER JOIN|Matching rows only|
|LEFT JOIN|All left table rows|
|RIGHT JOIN|All right table rows|
|FULL OUTER JOIN|All rows from both tables|
|SELF JOIN|Join table with itself|
|CROSS JOIN|Cartesian product|

---

# 1. INNER JOIN 🔥

Returns only matching rows from both tables.

---

# Syntax

```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

---

# Example

```sql
SELECT student.name, department.deptname
FROM student
INNER JOIN department
ON student.deptid = department.deptid;
```

---

# Output

|name|deptname|
|---|---|
|Arun|CSE|
|Neha|ECE|
|Rahul|CSE|

---

# How INNER JOIN Works 🧠

It checks matching `deptid` values in both tables.

Only matching records are displayed.

Non-matching rows are ignored.

---

# 2. LEFT JOIN ⬅️

Returns:

- all rows from left table
    
- matching rows from right table
    

If no match exists → NULL values shown.

---

# Syntax

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```

---

# Example

```sql
SELECT student.name, department.deptname
FROM student
LEFT JOIN department
ON student.deptid = department.deptid;
```

---

# Suppose Student Table Contains

|sid|name|deptid|
|---|---|---|
|4|Akhil|105|

No department 105 exists.

---

# Output

|name|deptname|
|---|---|
|Arun|CSE|
|Neha|ECE|
|Rahul|CSE|
|Akhil|NULL|

---

# Important Point 🚨

All rows from LEFT table are always displayed.

---

# 3. RIGHT JOIN ➡️

Returns:

- all rows from right table
    
- matching rows from left table
    

---

# Syntax

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```

---

# Example

```sql
SELECT student.name, department.deptname
FROM student
RIGHT JOIN department
ON student.deptid = department.deptid;
```

---

# Suppose Department Table Contains

|deptid|deptname|
|---|---|
|103|ME|

No student belongs to ME.

---

# Output

|name|deptname|
|---|---|
|Arun|CSE|
|Neha|ECE|
|Rahul|CSE|
|NULL|ME|

---

# Important Point 🚨

All rows from RIGHT table are always displayed.

---

# 4. FULL OUTER JOIN 🌍

Returns:

- all matching rows
    
- all non-matching rows from both tables
    

NULL shown where match does not exist.

---

# Syntax

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

---

# Output Example

|name|deptname|
|---|---|
|Arun|CSE|
|Neha|ECE|
|Rahul|CSE|
|Akhil|NULL|
|NULL|ME|

---

# Important Point 🚨

Combines LEFT JOIN + RIGHT JOIN results.

---

# 5. SELF JOIN 🔄

A table joined with itself.

Used when rows in same table are related.

---

# Example Table

|empid|empname|manager_id|
|---|---|---|
|1|Arun|NULL|
|2|Rahul|1|
|3|Neha|1|

---

# Example

```sql
SELECT A.empname AS Employee,
       B.empname AS Manager
FROM employee A
JOIN employee B
ON A.manager_id = B.empid;
```

---

# Output

|Employee|Manager|
|---|---|
|Rahul|Arun|
|Neha|Arun|

---

# 6. CROSS JOIN ✖️

Returns Cartesian product.

Every row from first table combines with every row from second table.

---

# Formula

\text{Rows in Result} = (\text{Rows in Table1}) \times (\text{Rows in Table2})

---

# Example

If:

- Table A has 3 rows
    
- Table B has 2 rows
    

Result = 6 rows.

---

# Syntax

```sql
SELECT *
FROM table1
CROSS JOIN table2;
```

---

# JOIN Keywords Summary ⚡

|Join|Returns|
|---|---|
|INNER JOIN|Matching rows only|
|LEFT JOIN|All left rows|
|RIGHT JOIN|All right rows|
|FULL OUTER JOIN|All rows from both|
|SELF JOIN|Same table join|
|CROSS JOIN|Cartesian product|

---

# INNER JOIN vs LEFT JOIN ⚔️

|INNER JOIN|LEFT JOIN|
|---|---|
|Matching rows only|All left rows|
|Ignores unmatched rows|Includes unmatched rows|

---

# Important Viva Questions 🎤

### Q1. What is JOIN in SQL?

Used to combine data from multiple tables.

---

### Q2. Why are joins used?

To retrieve related data from different tables.

---

### Q3. Which key is commonly used in joins?

FOREIGN KEY.

---

### Q4. What does INNER JOIN return?

Only matching rows.

---

### Q5. What does LEFT JOIN return?

All rows from left table and matching rows from right table.

---

### Q6. Difference between LEFT JOIN and RIGHT JOIN?

|LEFT JOIN|RIGHT JOIN|
|---|---|
|All left rows|All right rows|

---

### Q7. What is SELF JOIN?

A table joined with itself.

---

### Q8. What is CROSS JOIN?

Cartesian product of two tables.

---

### Q9. Which join returns all rows from both tables?

FULL OUTER JOIN.

---

### Q10. What is the condition used in joins?

`ON` clause.

---

# Common Exam Queries 💀

## INNER JOIN

```sql
SELECT student.name, department.deptname
FROM student
INNER JOIN department
ON student.deptid = department.deptid;
```

---

## LEFT JOIN

```sql
SELECT student.name, department.deptname
FROM student
LEFT JOIN department
ON student.deptid = department.deptid;
```

---

## RIGHT JOIN

```sql
SELECT student.name, department.deptname
FROM student
RIGHT JOIN department
ON student.deptid = department.deptid;
```

---

# Teacher Trap Questions 😭

### “Which join gives unmatched rows?”

LEFT JOIN / RIGHT JOIN / FULL OUTER JOIN

---

### “Which join may create huge number of rows?”

CROSS JOIN 💀

---

### “Can INNER JOIN show NULL unmatched rows?”

No.

---

# Quick Revision ⚡

|Join|Main Idea|
|---|---|
|INNER JOIN|Matching data|
|LEFT JOIN|Keep left table|
|RIGHT JOIN|Keep right table|
|FULL JOIN|Keep everything|
|SELF JOIN|Same table|
|CROSS JOIN|Every combination|

[[DBMS Lab Experiments]]