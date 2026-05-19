

`INSERT` is used to add records (rows) into a table.

---

# Syntax

## Insert All Values

```sql
INSERT INTO table_name
VALUES (value1, value2, value3);
```

---

# Example Table

|rollno|name|dept|
|---|---|---|
|Empty initially|||

---

# Example

```sql
INSERT INTO student
VALUES (101, 'Arun', 'CSE');
```

---

# What it does

Adds one row into the `student` table.

---

# Output

|rollno|name|dept|
|---|---|---|
|101|Arun|CSE|

---

# Insert Multiple Rows 🔥

```sql
INSERT INTO student
VALUES
(102, 'Neha', 'ECE'),
(103, 'Rahul', 'ME');
```

---

# Insert Specific Columns 🎯

```sql
INSERT INTO student (rollno, name)
VALUES (104, 'Anu');
```

---

# Why specify columns?

Useful when:

- not inserting all values
    
- changing column order
    

---

# Important Points 🚨

- Values must match datatype.
    
- Number of values should match columns.
    
- Strings must be inside quotes.
    

---

# Important Viva Questions 🎤

### Q1. What is INSERT command?

Used to add records into a table.

---

### Q2. Which language category does INSERT belong to?

DML (Data Manipulation Language).

---

### Q3. How do you insert a row into a table?

```sql
INSERT INTO student
VALUES (101, 'Arun', 'CSE');
```

---

### Q4. Can we insert values into selected columns?

Yes.

```sql
INSERT INTO student (rollno, name)
VALUES (105, 'Akhil');
```

---

### Q5. What happens if number of values is less/more?

DBMS gives an error.

---

### Q6. Why are strings written inside quotes?

Because they are character data.

---

### Q7. Does INSERT change table structure?

No. It only adds data.

---

### Q8. Difference between INSERT and SELECT?

|INSERT|SELECT|
|---|---|
|Adds data|Retrieves data|

---

### Q9. Can multiple rows be inserted at once?

Yes.

---

### Q10. What happens if datatype mismatches?

DBMS shows error.

```sql
INSERT INTO student
VALUES ('ABC', 'Arun', 'CSE');
```

If `rollno` is INT → error 💀