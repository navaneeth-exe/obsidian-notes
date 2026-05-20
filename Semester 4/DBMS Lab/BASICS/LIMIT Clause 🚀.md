

`LIMIT` is used to restrict the number of rows displayed in the output.

---

# Syntax

```sql
SELECT column_name
FROM table_name
LIMIT number;
```

---

# Example Table 🎓

|rollno|name|dept|
|---|---|---|
|101|Arun|CSE|
|102|Neha|ECE|
|103|Rahul|ME|
|104|Anu|CSE|

---

# Example 1 — Display First 2 Rows

```sql
SELECT *
FROM student
LIMIT 2;
```

---

# Output

|rollno|name|dept|
|---|---|---|
|101|Arun|CSE|
|102|Neha|ECE|

Only first 2 rows displayed.

---

# Example 2 — With WHERE Clause

```sql
SELECT *
FROM student
WHERE dept='CSE'
LIMIT 1;
```

Displays only one CSE student.

---

# Example 3 — With ORDER BY 🔥

```sql
SELECT *
FROM student
ORDER BY marks DESC
LIMIT 3;
```

Displays top 3 highest marks.

---

# Important Points 🚨

- Used to reduce output size
    
- Mostly used with `SELECT`
    
- Helpful for large tables
    

---

# Important Viva Questions 🎤

### Q1. What is LIMIT used for?

To restrict number of rows in output.

---

### Q2. Which command commonly uses LIMIT?

`SELECT`

---

### Q3. What does `LIMIT 5` mean?

Displays first 5 rows.

---

### Q4. Can LIMIT be used with ORDER BY?

Yes.

---

### Q5. Why is LIMIT useful?

To avoid displaying huge amounts of data.

---

# Common Exam Examples 💀

## Display first 3 students

```sql
SELECT *
FROM student
LIMIT 3;
```

---

## Display top 2 marks

```sql
SELECT *
FROM student
ORDER BY marks DESC
LIMIT 2;
```

---

# Teacher Trap Question 😭

### “Does LIMIT permanently delete rows?”

No 💀  
It only limits displayed output.

---

# Quick Revision ⚡

|Clause|Purpose|
|---|---|
|LIMIT|Restricts number of output rows|

[[DBMS Lab Experiments]]