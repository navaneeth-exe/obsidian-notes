
`TRUNCATE` is used to remove all rows from a table quickly.

It deletes entire data inside the table, but the table structure remains.

`TRUNCATE` belongs to DDL (Data Definition Language).

---

# Syntax

```sql
TRUNCATE TABLE table_name;
```

---

# Example Table 🎓

|rollno|name|dept|
|---|---|---|
|101|Arun|CSE|
|102|Neha|ECE|
|103|Rahul|ME|

---

# Example

```sql
TRUNCATE TABLE student;
```

---

# Output After TRUNCATE

|rollno|name|dept|
|---|---|---|
|No rows|||

All records removed 💀

But:

- table still exists
    
- columns still exist
    
- constraints still exist
    

---

# What TRUNCATE Does 🧠

- Removes all rows at once
    
- Resets storage space
    
- Faster than DELETE
    
- Cannot use WHERE clause
    

---

# Difference Between DELETE, TRUNCATE and DROP ⚔️

|DELETE|TRUNCATE|DROP|
|---|---|---|
|Deletes selected/all rows|Deletes all rows|Deletes entire table|
|WHERE can be used|WHERE not allowed|Removes structure also|
|Slower|Faster|Entire table removed|
|DML|DDL|DDL|

---

# DELETE vs TRUNCATE Example 🔥

## DELETE

```sql
DELETE FROM student
WHERE dept='CSE';
```

Deletes only matching rows.

---

## TRUNCATE

```sql
TRUNCATE TABLE student;
```

Deletes all rows directly.

---

# Important Points 🚨

- Removes all records
    
- Table structure remains
    
- Faster than DELETE
    
- WHERE clause cannot be used
    

---

# Important Viva Questions 🎤

### Q1. What is TRUNCATE command used for?

To remove all rows from a table quickly.

---

### Q2. Does TRUNCATE remove table structure?

No.

---

### Q3. Can WHERE clause be used with TRUNCATE?

No.

---

### Q4. Which is faster: DELETE or TRUNCATE?

TRUNCATE.

---

### Q5. Which language category does TRUNCATE belong to?

DDL.

---

### Q6. Difference between DELETE and TRUNCATE?

|DELETE|TRUNCATE|
|---|---|
|Removes selected rows|Removes all rows|
|WHERE allowed|WHERE not allowed|

---

### Q7. Difference between TRUNCATE and DROP?

|TRUNCATE|DROP|
|---|---|
|Removes data only|Removes table completely|

---

# Common Exam Queries 💀

## Remove all records

```sql
TRUNCATE TABLE employee;
```

---

## Remove all student data

```sql
TRUNCATE TABLE student;
```

---

# Teacher Trap Question 😭

### “Can TRUNCATE remove specific rows?”

No 💀  
Because WHERE clause is not allowed.

---

# Quick Revision ⚡

|Command|Purpose|
|---|---|
|DELETE|Remove selected rows|
|TRUNCATE|Remove all rows quickly|
|DROP|Remove entire table|

[[DBMS Lab Experiments]]