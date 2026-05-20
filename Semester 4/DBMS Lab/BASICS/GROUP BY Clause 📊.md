`GROUP BY` is used to group rows having the same values into a single group.

It is commonly used with aggregate functions like:

- `COUNT()`
    
- `SUM()`
    
- `AVG()`
    
- `MAX()`
    
- `MIN()`
    

`GROUP BY` helps in performing calculations on each group separately instead of the whole table.

---

# Syntax

```sql
SELECT column_name, aggregate_function(column_name)
FROM table_name
GROUP BY column_name;
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

# Example 1 — Average Marks Department Wise

```sql
SELECT dept, AVG(marks)
FROM student
GROUP BY dept;
```

---

# Output

|dept|AVG(marks)|
|---|---|
|CSE|80|
|ECE|82.5|

---

# What Happens Here? 🤔

Rows with same department are grouped together.

Then `AVG()` is calculated separately for each department.

---

# Example 2 — Count Students in Each Department

```sql
SELECT dept, COUNT(*)
FROM student
GROUP BY dept;
```

---

# Output

|dept|COUNT(*)|
|---|---|
|CSE|2|
|ECE|2|

---

# Example 3 — Find Maximum Marks in Each Department

```sql
SELECT dept, MAX(marks)
FROM student
GROUP BY dept;
```

---

# Output

|dept|MAX(marks)|
|---|---|
|CSE|90|
|ECE|85|

---

# GROUP BY with WHERE 🔥

`WHERE` filters rows before grouping.

```sql
SELECT dept, AVG(marks)
FROM student
WHERE marks > 75
GROUP BY dept;
```

---

# Important Rules 🚨

- Columns in `SELECT` should either:
    
    - be inside aggregate function
        
    - or appear in `GROUP BY`
        

---

# Wrong Query ❌

```sql
SELECT name, AVG(marks)
FROM student
GROUP BY dept;
```

Error may occur because `name` is neither grouped nor aggregated.

---

# Important Viva Questions 🎤

### Q1. What is GROUP BY used for?

To group rows with same values.

---

### Q2. Which functions are commonly used with GROUP BY?

Aggregate functions.

---

### Q3. Does GROUP BY return single row?

It returns one row per group.

---

### Q4. Which clause filters rows before grouping?

`WHERE`

---

### Q5. Difference between WHERE and GROUP BY?

|WHERE|GROUP BY|
|---|---|
|Filters rows|Groups rows|

---

### Q6. Can GROUP BY be used without aggregate functions?

Yes, but mainly used with them.

---

### Q7. Which clause is executed first: WHERE or GROUP BY?

`WHERE`

---

# Common Exam Queries 💀

## Count students department wise

```sql
SELECT dept, COUNT(*)
FROM student
GROUP BY dept;
```

---

## Find average marks department wise

```sql
SELECT dept, AVG(marks)
FROM student
GROUP BY dept;
```

---

## Find highest marks in each department

```sql
SELECT dept, MAX(marks)
FROM student
GROUP BY dept;
```

---

# Teacher Trap Question 😭

### “Can GROUP BY work without aggregate functions?”

Yes, but usually grouping is meaningful with aggregate functions.

---

# Quick Revision ⚡

|Clause|Purpose|
|---|---|
|GROUP BY|Groups similar rows|
|COUNT()|Counts rows in group|
|AVG()|Average of group|
|MAX()|Highest value in group|

[[DBMS Lab Experiments]]