
`DELETE` command is used to remove records (rows) from a table.

It deletes data based on a condition.

The table structure remains unchanged.

---

# Syntax

```sql
DELETE FROM table_name
WHERE condition;
```

---

# Example Table 🎓

|rollno|name|dept|
|---|---|---|
|101|Arun|CSE|
|102|Neha|ECE|
|103|Rahul|ME|

---

# Example 1 — Delete Single Row

```sql
DELETE FROM student
WHERE rollno = 102;
```

---

# Output

|rollno|name|dept|
|---|---|---|
|101|Arun|CSE|
|103|Rahul|ME|

Student with roll number 102 removed.

---

# Example 2 — Delete Multiple Rows

```sql
DELETE FROM student
WHERE dept='ME';
```

Deletes all students from ME department.

---

# Example 3 — Delete All Rows ⚠️

```sql
DELETE FROM student;
```

---

# What Happens? 💀

All records are deleted, but:

- table structure remains
    
- columns remain
    
- constraints remain
    

---

# Difference Between DELETE, DROP and TRUNCATE ⚔️

|DELETE|TRUNCATE|DROP|
|---|---|---|
|Deletes rows|Deletes all rows|Deletes entire table|
|Structure remains|Structure remains|Structure removed|
|Uses WHERE|No WHERE|Removes table completely|

---

# DELETE with AND Operator 🔥

```sql
DELETE FROM student
WHERE dept='CSE' AND marks < 40;
```

Deletes CSE students with marks less than 40.

---

# Important Points 🚨

- Removes records only
    
- Table structure remains
    
- `WHERE` clause is important
    
- Without `WHERE`, all rows are deleted
    

---

# Important Viva Questions 🎤

### Q1. What is DELETE command used for?

To remove records from a table.

---

### Q2. Which clause selects rows to delete?

`WHERE`

---

### Q3. What happens if WHERE clause is omitted?

All rows are deleted.

---

### Q4. Does DELETE remove table structure?

No.

---

### Q5. Which language category does DELETE belong to?

DML (Data Manipulation Language).

---

### Q6. Difference between DELETE and DROP?

|DELETE|DROP|
|---|---|
|Deletes rows|Deletes entire table|

---

### Q7. Difference between DELETE and TRUNCATE?

|DELETE|TRUNCATE|
|---|---|
|Can use WHERE|Cannot use WHERE|

---

# Common Exam Queries 💀

## Delete one student

```sql
DELETE FROM student
WHERE rollno = 101;
```

---

## Delete ECE students

```sql
DELETE FROM student
WHERE dept='ECE';
```

---

## Delete all records

```sql
DELETE FROM student;
```

---

# Teacher Trap Question 😭

### “What is dangerous in DELETE command?”

Forgetting `WHERE` clause 💀

---

# Quick Revision ⚡

|Keyword|Purpose|
|---|---|
|DELETE|Remove records|
|WHERE|Select rows to delete|
|DROP|Remove entire table|
|TRUNCATE|Remove all rows|

[[DBMS Lab Experiments]]