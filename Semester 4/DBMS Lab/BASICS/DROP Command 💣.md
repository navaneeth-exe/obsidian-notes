# DROP Command 💣

`DROP` is a DDL (Data Definition Language) command used to permanently remove database objects.

It can delete:

- Tables
    
- Databases
    
- Views
    

Once dropped → structure + data both gone 💀

---

# Syntax

## Drop a Table

```sql
DROP TABLE table_name;
```

---

## Example

```sql
DROP TABLE student;
```

### What it does

Deletes the entire `student` table including:

- all records
    
- structure
    
- constraints
    

---

# Before DROP

|RollNo|Name|
|---|---|
|101|Arun|
|102|Neha|

---

# After DROP

❌ Table no longer exists.

Trying to access it gives error.

---

# Drop Database

```sql
DROP DATABASE College;
```

### What it does

Deletes the complete database permanently.

Everything inside it gets removed 😭

---

# DROP vs DELETE vs TRUNCATE ⚔️

|DROP|DELETE|TRUNCATE|
|---|---|---|
|Removes entire table|Removes selected rows|Removes all rows|
|Structure deleted|Structure remains|Structure remains|
|Cannot rollback usually|Can rollback|Usually cannot rollback|
|Fast|Slower|Faster|

---

# Example Comparison

---

## DELETE

```sql
DELETE FROM student
WHERE rollno = 101;
```

👉 Removes only one row.

---

## TRUNCATE

```sql
TRUNCATE TABLE student;
```

👉 Removes all rows but table exists.

---

## DROP

```sql
DROP TABLE student;
```

👉 Removes everything permanently.

---

# Important Points 🚨

- DROP frees memory space.
    
- Structure and data both deleted.
    
- Cannot use table again unless recreated.
    
- Mostly irreversible.
    

---

# Possible Viva Questions 🎤

## Q1. What is DROP command?

Used to permanently remove database objects.

---

## Q2. Which category does DROP belong to?

DDL.

---

## Q3. What happens when a table is dropped?

Both structure and data are deleted.

---

## Q4. Difference between DROP and DELETE?

|DROP|DELETE|
|---|---|
|Deletes table completely|Deletes rows only|

---

## Q5. Difference between DROP and TRUNCATE?

|DROP|TRUNCATE|
|---|---|
|Removes table completely|Removes only records|

---

## Q6. Can we recover dropped table?

Normally no unless backup/recycle bin exists.

---

## Q7. Does DROP remove constraints and indexes?

Yes.

---

## Q8. Is WHERE clause used with DROP?

No.

---

# Teacher Favorite Confusing Question 😭

### “Which command removes structure but DELETE does not?”

Answer:  
`DROP`

---

# Mini Revision ⚡

| Command | Purpose                   |
| ------- | ------------------------- |
| CREATE  | Create object             |
| ALTER   | Modify structure          |
| DROP    | Delete object permanently |



[[DBMS Lab Experiments]]