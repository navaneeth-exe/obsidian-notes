
`HAVING` clause is used to filter groups created by `GROUP BY`.

It is mainly used with aggregate functions.

While `WHERE` filters rows, `HAVING` filters groups.

---

# Syntax

```sql
SELECT column_name, aggregate_function(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

---

# Example Table 🎓

|rollno|name|dept|marks|
|---|---|---|---|
|101|Arun|CSE|90|
|102|Neha|ECE|85|
|103|Rahul|CSE|70|
|104|Anu|ECE|80|

---

# Example 1 — Average Marks Greater Than 80

```sql
SELECT dept, AVG(marks)
FROM student
GROUP BY dept
HAVING AVG(marks) > 80;
```

---

# Output

|dept|AVG(marks)|
|---|---|
|ECE|82.5|

---

# What Happens Here? 🤔

1. Rows are grouped department-wise
    
2. Average marks calculated for each group
    
3. `HAVING` filters groups where average > 80
    

---

# Example 2 — Departments with More Than 1 Student

```sql
SELECT dept, COUNT(*)
FROM student
GROUP BY dept
HAVING COUNT(*) > 1;
```

---

# Output

|dept|COUNT(*)|
|---|---|
|CSE|2|
|ECE|2|

---

# WHERE vs HAVING ⚔️

|WHERE|HAVING|
|---|---|
|Filters rows|Filters groups|
|Used before grouping|Used after grouping|
|Cannot use aggregate functions directly|Can use aggregate functions|

---

# Example Using WHERE + HAVING 🔥

```sql
SELECT dept, AVG(marks)
FROM student
WHERE marks > 70
GROUP BY dept
HAVING AVG(marks) > 80;
```

---

# Execution Order 🧠

1. WHERE
    
2. GROUP BY
    
3. HAVING
    
4. SELECT
    
5. ORDER BY
    

---

# Important Points 🚨

- `HAVING` usually used with `GROUP BY`
    
- Works mainly with aggregate functions
    
- Filters grouped data
    

---

# Important Viva Questions 🎤

### Q1. What is HAVING clause used for?

To filter grouped data.

---

### Q2. Difference between WHERE and HAVING?

|WHERE|HAVING|
|---|---|
|Filters rows|Filters groups|

---

### Q3. Which clause is used with aggregate functions?

`HAVING`

---

### Q4. Is HAVING used before or after GROUP BY?

After GROUP BY.

---

### Q5. Can HAVING be used without GROUP BY?

Yes, but uncommon.

---

### Q6. Which clause filters rows before grouping?

`WHERE`

---

# Common Exam Queries 💀

## Departments with average marks above 80

```sql
SELECT dept, AVG(marks)
FROM student
GROUP BY dept
HAVING AVG(marks) > 80;
```

---

## Departments having more than 2 students

```sql
SELECT dept, COUNT(*)
FROM student
GROUP BY dept
HAVING COUNT(*) > 2;
```

---

# Teacher Trap Question 😭

### “Can aggregate functions be used in WHERE clause?”

Usually no.

Wrong ❌

```sql
WHERE AVG(marks) > 80
```

Correct ✅

```sql
HAVING AVG(marks) > 80
```

---

# Quick Revision ⚡

|Clause|Purpose|
|---|---|
|WHERE|Filters rows|
|GROUP BY|Groups rows|
|HAVING|Filters groups|

[[DBMS Lab Experiments]]