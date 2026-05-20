
`WHERE` clause is used to filter records based on a condition.

It displays only the rows that satisfy the condition.

---

# Syntax

```sql
SELECT column_name
FROM table_name
WHERE condition;
```

---

# Example Table 🎓

|rollno|name|dept|marks|
|---|---|---|---|
|101|Arun|CSE|90|
|102|Neha|ECE|85|
|103|Rahul|CSE|70|

---

# Example 1 — Single Condition

```sql
SELECT *
FROM student
WHERE dept = 'CSE';
```

---

## Output

|rollno|name|dept|marks|
|---|---|---|---|
|101|Arun|CSE|90|
|103|Rahul|CSE|70|

Only CSE students displayed.

---

# Example 2 — Numeric Condition

```sql
SELECT *
FROM student
WHERE marks > 80;
```

---

## Output

|rollno|name|marks|
|---|---|---|
|101|Arun|90|
|102|Neha|85|

---

# Using AND Operator 🔥

```sql
SELECT *
FROM student
WHERE dept = 'CSE' AND marks > 80;
```

Both conditions must be true.

---

# Using OR Operator

```sql
SELECT *
FROM student
WHERE dept = 'CSE' OR dept = 'ECE';
```

Any one condition true = row displayed.

---

# Using NOT Operator 🚫

```sql
SELECT *
FROM student
WHERE NOT dept = 'CSE';
```

Displays non-CSE students.

---

# Using LIKE 🔍

Used for pattern matching.

```sql
SELECT *
FROM student
WHERE name LIKE 'A%';
```

Names starting with `A`.

---

# Wildcards in LIKE

|Symbol|Meaning|
|---|---|
|%|Any number of characters|
|_|Single character|

---

# BETWEEN Operator

```sql
SELECT *
FROM student
WHERE marks BETWEEN 70 AND 90;
```

---

# IN Operator

```sql
SELECT *
FROM student
WHERE dept IN ('CSE', 'ECE');
```

---

# Important Viva Questions 🎤

### Q1. What is WHERE clause used for?

To filter rows based on condition.

---

### Q2. Which command is commonly used with WHERE?

`SELECT`

---

### Q3. Which operators are used with WHERE?

- AND
    
- OR
    
- NOT
    
- LIKE
    
- BETWEEN
    
- IN
    

---

### Q4. Difference between WHERE and HAVING?

|WHERE|HAVING|
|---|---|
|Filters rows|Filters groups|

---

### Q5. What does LIKE do?

Pattern matching.

---

### Q6. What does `%` mean in LIKE?

Represents multiple characters.

---

### Q7. What happens if WHERE condition matches nothing?

Empty result returned.

---

### Q8. Can WHERE be used without SELECT?

Yes, with UPDATE and DELETE also.

Example:

```sql
DELETE FROM student
WHERE rollno = 101;
```

---

# Common Exam Queries 💀

## Display CSE students

```sql
SELECT * FROM student
WHERE dept = 'CSE';
```

---

## Display students with marks above 80

```sql
SELECT * FROM student
WHERE marks > 80;
```

---

## Display names starting with A

```sql
SELECT * FROM student
WHERE name LIKE 'A%';
```

---

# Teacher Trap Question 😭

### “Does WHERE permanently remove rows?”

No. It only filters query output unless used with DELETE/UPDATE.

---

# Quick Revision ⚡

|Clause|Purpose|
|---|---|
|WHERE|Filters rows|
|AND|Both conditions true|
|OR|Any condition true|
|LIKE|Pattern matching|
|BETWEEN|Range checking|



[[DBMS Lab Experiments]]