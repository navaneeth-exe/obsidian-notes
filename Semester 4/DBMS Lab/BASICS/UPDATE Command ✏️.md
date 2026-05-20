
`UPDATE` command is used to modify existing data in a table.

It changes values of one or more rows based on a condition.

---

# Syntax

```sql
UPDATE table_name
SET column_name = value
WHERE condition;
```

---

# Example Table 🎓

|rollno|name|dept|marks|
|---|---|---|---|
|101|Arun|CSE|90|
|102|Neha|ECE|85|
|103|Rahul|ME|70|

---

# Example 1 — Update Single Row

```sql
UPDATE student
SET marks = 95
WHERE rollno = 101;
```

---

# Output

|rollno|name|marks|
|---|---|---|
|101|Arun|95|

Marks changed from 90 → 95 🔥

---

# Example 2 — Update Multiple Columns

```sql
UPDATE student
SET dept = 'CSE', marks = 80
WHERE rollno = 103;
```

---

# What it does

- Changes dept to CSE
    
- Changes marks to 80
    

for roll number 103.

---

# Example 3 — Update All Rows ⚠️

```sql
UPDATE student
SET marks = 100;
```

---

# What Happens? 💀

All rows get updated because no `WHERE` clause is used.

---

# Before Update

|rollno|marks|
|---|---|
|101|90|
|102|85|

---

# After Update

|rollno|marks|
|---|---|
|101|100|
|102|100|

---

# Using Arithmetic Operators 🔢

```sql
UPDATE student
SET marks = marks + 5
WHERE dept='CSE';
```

Adds 5 marks to CSE students.

---

# Important Points 🚨

- `SET` specifies new value
    
- `WHERE` specifies which rows to update
    
- Without `WHERE`, all rows are updated
    

---

# Important Viva Questions 🎤

### Q1. What is UPDATE command used for?

To modify existing records in a table.

---

### Q2. Which clause specifies new values?

`SET`

---

### Q3. Which clause selects rows to update?

`WHERE`

---

### Q4. What happens if WHERE clause is omitted?

All rows are updated.

---

### Q5. Which language category does UPDATE belong to?

DML (Data Manipulation Language).

---

### Q6. Can multiple columns be updated together?

Yes.

---

### Q7. Does UPDATE change table structure?

No. It only changes data.

---

# Common Exam Queries 💀

## Update marks of one student

```sql
UPDATE student
SET marks = 90
WHERE rollno = 102;
```

---

## Change department

```sql
UPDATE student
SET dept='ECE'
WHERE rollno = 101;
```

---

## Increase salary by 10%

```sql
UPDATE employee
SET salary = salary + (salary * 0.10);
```

---

# Teacher Trap Question 😭

### “Which clause is dangerous to forget in UPDATE?”

`WHERE`

Because forgetting it updates entire table 💀

---

# Quick Revision ⚡

|Keyword|Purpose|
|---|---|
|UPDATE|Modify records|
|SET|Assign new values|
|WHERE|Select rows to update|

[[DBMS Lab Experiments]]