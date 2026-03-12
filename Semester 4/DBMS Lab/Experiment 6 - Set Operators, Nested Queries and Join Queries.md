# 1️⃣ Aim of the Experiment

To implement **set operators, nested queries, and join queries** to retrieve and combine data from one or more tables.

These techniques are used to perform **advanced SQL data retrieval operations**.

---

# 2️⃣ Concepts Used

This experiment demonstrates:

- Set operators
    
- Join operations
    
- Nested queries (subqueries)
    
- Data retrieval from multiple tables
    

Main SQL techniques used:

|Concept|Purpose|
|---|---|
|Set Operators|Combine results from multiple queries|
|Joins|Retrieve related data from multiple tables|
|Nested Queries|Query inside another query|

---

# 3️⃣ Set Operators

Set operators combine results of **two or more SELECT queries**.

Important rule:

Both queries must have:

- Same number of columns
    
- Compatible data types
    

---

# UNION

```
SELECT name FROM Course_A  
UNION  
SELECT name FROM Course_B;
```

Explanation:

UNION combines results from both tables **and removes duplicates**.

Course_A

|name|
|---|
|Arun|
|Bala|
|Charan|

Course_B

|name|
|---|
|Bala|
|Divya|

Result:

|name|
|---|
|Arun|
|Bala|
|Charan|
|Divya|

Duplicate **Bala removed**.

---

# UNION ALL

```
SELECT name FROM Course_A  
UNION ALL  
SELECT name FROM Course_B;
```

Explanation:

UNION ALL combines results **including duplicates**.

Result:

|name|
|---|
|Arun|
|Bala|
|Charan|
|Bala|
|Divya|

Duplicate **Bala appears twice**.

---

# INTERSECT (MySQL Workaround)

MySQL doesn't support **INTERSECT** directly.

So we use:

```
SELECT name FROM Course_A  
WHERE name IN (SELECT name FROM Course_B);
```

Explanation:

This returns **common records**.

Result:

|name|
|---|
|Bala|

---

# EXCEPT (MySQL Workaround)

MySQL doesn't support **EXCEPT**, so we use **NOT IN**.

```
SELECT name FROM Course_A  
WHERE name NOT IN (SELECT name FROM Course_B);
```
Explanation:

Returns records in **Course_A but not in Course_B**.

Result:

|name|
|---|
|Arun|
|Charan|

---

# 4️⃣ Join Queries

Joins are used to **combine data from multiple tables using a common column**.

Example tables:

Employee

|emp_id|emp_name|dept_id|
|---|---|---|
|1|Arun|101|
|2|Bala|102|
|3|Charan|103|

Department

|dept_id|dept_name|
|---|---|
|101|HR|
|102|IT|
|104|Finance|

---

# INNER JOIN

```
SELECT emp_name, dept_name  
FROM Employee  
INNER JOIN Department  
ON Employee.dept_id = Department.dept_id;
```

Explanation:

Returns only rows where **dept_id matches in both tables**.

Result:

|emp_name|dept_name|
|---|---|
|Arun|HR|
|Bala|IT|

Charan excluded because dept_id **103 not in Department table**.

---

# LEFT JOIN

```
SELECT emp_name, dept_name  
FROM Employee  
LEFT JOIN Department  
ON Employee.dept_id = Department.dept_id;
```

Explanation:

Returns:

- All rows from **Employee table**
    
- Matching rows from Department
    

Result:

|emp_name|dept_name|
|---|---|
|Arun|HR|
|Bala|IT|
|Charan|NULL|

NULL appears when no matching department exists.

---

# RIGHT JOIN

```
SELECT emp_name, dept_name  
FROM Employee  
RIGHT JOIN Department  
ON Employee.dept_id = Department.dept_id;
```
Explanation:

Returns:

- All rows from **Department table**
    
- Matching rows from Employee
    

Result:

|emp_name|dept_name|
|---|---|
|Arun|HR|
|Bala|IT|
|NULL|Finance|

NULL means no employee in Finance department.

---

# 5️⃣ Nested Queries (Subqueries)

A nested query is a **query inside another query**.

Syntax:

```
SELECT column  
FROM table  
WHERE condition (  
    SELECT column FROM table  
);
```
---

# Example 1

Find employees in IT department.

```
SELECT emp_name  
FROM Employee  
WHERE dept_id IN (  
SELECT dept_id  
FROM Department  
WHERE dept_name = 'IT'  
);
```

Explanation:

Inner query finds dept_id of IT.

Outer query finds employees with that dept_id.

Result:

|emp_name|
|---|
|Bala|

---

# Example 2

Employees whose department does not exist.

```
SELECT emp_name  
FROM Employee  
WHERE dept_id NOT IN (  
SELECT dept_id FROM Department  
);
```

Result:

|emp_name|
|---|
|Charan|

Because dept_id **103 not in Department table**.

---

# Example 3

Find employees in HR department.

```
SELECT emp_name  
FROM Employee  
WHERE dept_id = (  
SELECT dept_id  
FROM Department  
WHERE dept_name = 'HR'  
);
```

Result:

|emp_name|
|---|
|Arun|

---

# 6️⃣ Result

Set operators, join queries, and nested queries were successfully implemented to retrieve and combine data from multiple tables.

---

# 7️⃣ Possible Viva Questions (With Answers)

---

### Q1. What are set operators?

**Answer**

Set operators combine results from multiple SELECT queries.

Examples:

- UNION
    
- UNION ALL
    
- INTERSECT
    
- EXCEPT
    

---

### Q2. Difference between UNION and UNION ALL?

|UNION|UNION ALL|
|---|---|
|Removes duplicates|Keeps duplicates|

---

### Q3. What is a JOIN?

**Answer**

A JOIN retrieves related data from multiple tables based on a common column.

---

### Q4. What is INNER JOIN?

**Answer**

INNER JOIN returns only records that match in both tables.

---

### Q5. What is LEFT JOIN?

**Answer**

LEFT JOIN returns all records from the left table and matching records from the right table.

---

### Q6. What is RIGHT JOIN?

**Answer**

RIGHT JOIN returns all records from the right table and matching records from the left table.

---

### Q7. What is a nested query?

**Answer**

A nested query (subquery) is a query inside another SQL query.

---

### Q8. Why do we use subqueries?

**Answer**

Subqueries help retrieve data based on the result of another query.

---

### Q9. Why is INTERSECT not used in MySQL?

**Answer**

Because MySQL does not support INTERSECT directly.

Instead we use:

IN

---

### Q10. Why is EXCEPT not used in MySQL?

**Answer**

MySQL does not support EXCEPT, so we use:

NOT IN

---

# 8️⃣ Tricky Viva Questions

---

### Q: Which join returns all rows from both tables?

Answer:

FULL OUTER JOIN (not supported in MySQL).

---

### Q: What happens if there is no matching value in join?

Answer:

JOIN may return **NULL values** depending on join type.

---

### Q: Can we join more than two tables?

Answer:

Yes, multiple tables can be joined in a single query.

### Q: Which join is used most frequently?

Answer:

INNER JOIN.