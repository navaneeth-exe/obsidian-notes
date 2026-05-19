

`SELECT` is used to retrieve/fetch data from a table.

This is probably the most used SQL command ever 😭

---

# Basic Syntax

```sql
SELECT column_name
FROM table_name;
```

---

# Example Table 🎓

## Student Table

|rollno|name|dept|
|---|---|---|
|101|Arun|CSE|
|102|Neha|ECE|
|103|Rahul|CSE|

---

# 1. Select All Columns ⭐

```sql
SELECT * FROM student;
```

---

## What it does

Displays all rows and all columns.

---

## Output

|rollno|name|dept|
|---|---|---|
|101|Arun|CSE|
|102|Neha|ECE|
|103|Rahul|CSE|

---

# 2. Select Specific Columns 🎯

```sql
SELECT name, dept
FROM student;
```

---

## Output

|name|dept|
|---|---|
|Arun|CSE|
|Neha|ECE|
|Rahul|CSE|

---

# 3. Using WHERE Clause 🔥

Used to filter records.

```sql
SELECT *
FROM student
WHERE dept = 'CSE';
```

---

## Output

|rollno|name|dept|
|---|---|---|
|101|Arun|CSE|
|103|Rahul|CSE|

---

# 4. Using AND Operator

```sql
SELECT *
FROM student
WHERE dept = 'CSE' AND rollno = 101;
```

---

# 5. Using OR Operator

```sql
SELECT *
FROM student
WHERE dept = 'CSE' OR dept = 'ECE';
```

---

# 6. Using ORDER BY 📈

Sorts records.

```sql
SELECT *
FROM student
ORDER BY name;
```

---

## Descending Order

```sql
SELECT *
FROM student
ORDER BY rollno DESC;
```

---

# 7. DISTINCT Keyword ✨

Removes duplicate values.

```sql
SELECT DISTINCT dept
FROM student;
```

---

## Output

|dept|
|---|
|CSE|
|ECE|

---

# 8. LIMIT Clause 🚀

Displays limited rows.

```sql
SELECT *
FROM student
LIMIT 2;
```

---

# 9. COUNT Function 🔢

Counts records.

```sql
SELECT COUNT(*)
FROM student;
```

---

# 10. Aliasing using AS 🎭

```sql
SELECT name AS Student_Name
FROM student;
```

---

# Possible Viva Questions 🎤

## Q1. What is SELECT command?

Used to retrieve data from a table.

---

## Q2. What does `SELECT *` mean?

Selects all columns.

---

## Q3. Which clause filters rows?

`WHERE`

---

## Q4. Difference between WHERE and HAVING?

|WHERE|HAVING|
|---|---|
|Filters rows|Filters groups|

---

## Q5. What is DISTINCT used for?

Removes duplicate values.

---

## Q6. Which clause sorts data?

`ORDER BY`

---

## Q7. What is default sorting order?

Ascending.

---

## Q8. Which keyword gives descending order?

`DESC`

---

## Q9. What does COUNT(*) do?

Counts total rows.

---

## Q10. Can SELECT work without WHERE?

Yes.

---

# Common Exam Queries 💀

---

## Display all students

```sql
SELECT * FROM student;
```

---

## Display only names

```sql
SELECT name FROM student;
```

---

## Display CSE students

```sql
SELECT * FROM student
WHERE dept = 'CSE';
```

---

## Sort by name

```sql
SELECT * FROM student
ORDER BY name;
```

---

# Teacher Trap Questions 😭

### “Does SELECT modify data?”

No. It only retrieves data.

---

### “Can SELECT retrieve specific columns?”

Yes.

---

### “What happens if WHERE condition matches nothing?”

Empty result shown.

---

# Quick Revision ⚡

|Command|Purpose|
|---|---|
|SELECT|Retrieve data|
|WHERE|Filter rows|
|ORDER BY|Sort rows|
|DISTINCT|Remove duplicates|
|COUNT|Count rows|