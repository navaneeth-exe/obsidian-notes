
Aggregate functions are SQL functions used to perform calculations on multiple rows of a table and return a single result.

They are mainly used for:

- calculations
    
- data analysis
    
- summarizing records
    

Aggregate functions are commonly used with:

- `SELECT`
    
- `WHERE`
    
- `GROUP BY`
    

---

# Common Aggregate Functions 📚

|Function|Purpose|
|---|---|
|COUNT()|Counts rows|
|SUM()|Adds values|
|AVG()|Finds average|
|MAX()|Finds highest value|
|MIN()|Finds lowest value|

---

# Example Table 🎓

|rollno|name|dept|marks|
|---|---|---|---|
|101|Arun|CSE|90|
|102|Neha|ECE|85|
|103|Rahul|CSE|70|

---

# 1. COUNT() 🔢

`COUNT()` is used to count the number of rows or values in a column.

---

## Syntax

```sql
SELECT COUNT(column_name)
FROM table_name;
```

---

## Example

```sql
SELECT COUNT(*)
FROM student;
```

---

## Output

|COUNT(*)|
|---|
|3|

---

## Important Points

- `COUNT(*)` counts all rows
    
- `COUNT(column_name)` ignores NULL values
    

---

# 2. SUM() ➕

`SUM()` calculates the total of numeric values in a column.

---

## Syntax

```sql
SELECT SUM(column_name)
FROM table_name;
```

---

## Example

```sql
SELECT SUM(marks)
FROM student;
```

---

## Output

|SUM(marks)|
|---|
|245|

---

# 3. AVG() 📊

`AVG()` returns the average value of a numeric column.

---

## Syntax

```sql
SELECT AVG(column_name)
FROM table_name;
```

---

## Example

```sql
SELECT AVG(marks)
FROM student;
```

---

## Output

|AVG(marks)|
|---|
|81.67|

---

Average is calculated as:

\text{Average} = \frac{\text{Sum of values}}{\text{Number of values}}

---

# 4. MAX() ⬆️

`MAX()` returns the largest value in a column.

---

## Syntax

```sql
SELECT MAX(column_name)
FROM table_name;
```

---

## Example

```sql
SELECT MAX(marks)
FROM student;
```

---

## Output

|MAX(marks)|
|---|
|90|

---

# 5. MIN() ⬇️

`MIN()` returns the smallest value in a column.

---

## Syntax

```sql
SELECT MIN(column_name)
FROM table_name;
```

---

## Example

```sql
SELECT MIN(marks)
FROM student;
```

---

## Output

|MIN(marks)|
|---|
|70|

---

# Using Aggregate Functions with WHERE 🔥

```sql
SELECT AVG(marks)
FROM student
WHERE dept='CSE';
```

Calculates average marks only for CSE students.

---

# Important Viva Questions 🎤

### Q1. What are aggregate functions?

Functions that perform calculations on multiple rows and return a single value.

---

### Q2. Which function counts rows?

`COUNT()`

---

### Q3. Which function finds average?

`AVG()`

---

### Q4. Which function finds maximum value?

`MAX()`

---

### Q5. Which function finds minimum value?

`MIN()`

---

### Q6. Which function calculates total values?

`SUM()`

---

### Q7. Can aggregate functions be used with WHERE clause?

Yes.

---

### Q8. Which function counts all rows including NULL values?

`COUNT(*)`

---

# Common Exam Queries 💀

## Count total students

```sql
SELECT COUNT(*)
FROM student;
```

---

## Find average marks

```sql
SELECT AVG(marks)
FROM student;
```

---

## Find highest marks

```sql
SELECT MAX(marks)
FROM student;
```

---

## Find total marks

```sql
SELECT SUM(marks)
FROM student;
```

---

# Quick Revision ⚡

|Function|Purpose|
|---|---|
|COUNT()|Count rows|
|SUM()|Add values|
|AVG()|Average|
|MAX()|Highest value|
|MIN()|Lowest value|

[[DBMS Lab Experiments]]