
`ORDER BY` is used to sort records in ascending or descending order.

---

# Syntax

```sql
SELECT column_name
FROM table_name
ORDER BY column_name;
```

---

# Example Table 🎓

|rollno|name|marks|
|---|---|---|
|103|Rahul|70|
|101|Arun|90|
|102|Neha|85|

---

# 1. Ascending Order (Default) ⬆️

```sql
SELECT *
FROM student
ORDER BY rollno;
```

---

# Output

|rollno|name|
|---|---|
|101|Arun|
|102|Neha|
|103|Rahul|

Smallest to largest.

---

# 2. Descending Order ⬇️

```sql
SELECT *
FROM student
ORDER BY marks DESC;
```

---

# Output

|name|marks|
|---|---|
|Arun|90|
|Neha|85|
|Rahul|70|

Largest to smallest.

---

# Using ASC Explicitly

```sql
SELECT *
FROM student
ORDER BY name ASC;
```

`ASC` = Ascending order.

---

# Sorting Multiple Columns 🔥

```sql
SELECT *
FROM student
ORDER BY dept, marks DESC;
```

First sorts by department, then marks.

---

# Important Points 🚨

- Default order is ascending
    
- `DESC` used for descending
    
- Mostly used with `SELECT`
    

---

# Important Viva Questions 🎤

### Q1. What is ORDER BY used for?

To sort records.

---

### Q2. What is default sorting order?

Ascending (`ASC`).

---

### Q3. Which keyword gives descending order?

`DESC`

---

### Q4. Can ORDER BY sort multiple columns?

Yes.

---

### Q5. Which command commonly uses ORDER BY?

`SELECT`

---

### Q6. Difference between ASC and DESC?

|ASC|DESC|
|---|---|
|Ascending|Descending|

---

# Common Exam Examples 💀

## Sort by name

```sql
SELECT *
FROM student
ORDER BY name;
```

---

## Sort by highest marks

```sql
SELECT *
FROM student
ORDER BY marks DESC;
```

---

# Teacher Trap Question 😭

### “Does ORDER BY permanently arrange table data?”

No.  
It only sorts query output.

---

# Quick Revision ⚡

|Clause|Purpose|
|---|---|
|ORDER BY|Sort records|
|ASC|Ascending order|
|DESC|Descending order|

[[DBMS Lab Experiments]]