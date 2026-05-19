
`DISTINCT` is used to remove duplicate values from the output.

It shows only unique values.

---

# Syntax

```sql
SELECT DISTINCT column_name
FROM table_name;
```

---

# Example Table 🎓

|rollno|name|dept|
|---|---|---|
|101|Arun|CSE|
|102|Neha|ECE|
|103|Rahul|CSE|
|104|Anu|ECE|

---

# Without DISTINCT ❌

```sql
SELECT dept FROM student;
```

---

## Output

|dept|
|---|
|CSE|
|ECE|
|CSE|
|ECE|

Duplicates appear.

---

# With DISTINCT ✅

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

Duplicate values removed 🔥

---

# DISTINCT on Multiple Columns

```sql
SELECT DISTINCT dept, name
FROM student;
```

Removes duplicate combinations of `dept + name`.

---

# Important Points 🚨

- Used with `SELECT`
    
- Removes duplicate records
    
- Mainly used for filtering repeated values
    

---

# Important Viva Questions 🎤

### Q1. What is DISTINCT used for?

To remove duplicate values from output.

---

### Q2. Does DISTINCT modify original table?

No. It only changes displayed result.

---

### Q3. Which command is used with DISTINCT?

`SELECT`

---

### Q4. Can DISTINCT be used on multiple columns?

Yes.

---

### Q5. Difference between DISTINCT and UNIQUE?

|DISTINCT|UNIQUE|
|---|---|
|Used in SELECT output|Used as constraint|

---

### Q6. What happens without DISTINCT?

Duplicate values appear.

---

### Q7. Is DISTINCT a constraint?

No.

---

# Common Exam Example 💀

```sql
SELECT DISTINCT city
FROM customer;
```

Displays only unique city names.

---

# Teacher Trap Question 😭

### “Does DISTINCT remove duplicates permanently?”

No. Only in query result.

---

# Quick Revision ⚡

|Keyword|Purpose|
|---|---|
|DISTINCT|Removes duplicate output values|