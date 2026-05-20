
`ALTER` command is used to modify the structure of an existing table.

Using `ALTER`, we can:

- add columns
    
- modify columns
    
- delete columns
    
- rename columns
    
- rename table
    
- add constraints
    

`ALTER` belongs to DDL (Data Definition Language).

---

# Basic Syntax

```sql
ALTER TABLE table_name
operation;
```

---

# Example Table 🎓

|rollno|name|dept|
|---|---|---|
|101|Arun|CSE|
|102|Neha|ECE|

---

# 1. ADD COLUMN ➕

Used to add new column to an existing table.

---

## Syntax

```sql
ALTER TABLE table_name
ADD column_name datatype;
```

---

## Example

```sql
ALTER TABLE student
ADD age INT;
```

---

# Output Structure

|rollno|name|dept|age|
|---|---|---|---|
|101|Arun|CSE|NULL|

New column added.

---

# 2. MODIFY COLUMN ✏️

Used to change datatype or size of a column.

---

## Syntax

```sql
ALTER TABLE table_name
MODIFY column_name new_datatype;
```

---

## Example

```sql
ALTER TABLE student
MODIFY name VARCHAR(50);
```

---

# What it does

Changes size of `name` column from old size to 50.

---

# 3. DROP COLUMN ❌

Used to remove a column from table.

---

## Syntax

```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

---

## Example

```sql
ALTER TABLE student
DROP COLUMN age;
```

---

# What Happens? 💀

`age` column permanently removed.

---

# 4. RENAME COLUMN 🏷️

Used to rename a column.

---

## Syntax

```sql
ALTER TABLE table_name
RENAME COLUMN old_name TO new_name;
```

---

## Example

```sql
ALTER TABLE student
RENAME COLUMN name TO student_name;
```

---

# Output Structure

|rollno|student_name|dept|
|---|---|---|

Column name changed.

---

# 5. RENAME TABLE 📂

Used to rename entire table.

---

## Syntax

```sql
ALTER TABLE old_table_name
RENAME TO new_table_name;
```

---

## Example

```sql
ALTER TABLE student
RENAME TO students;
```

---

# What it does

Changes table name from `student` → `students`.

---

# 6. ADD CONSTRAINT 🔒

Used to add constraints to existing table.

---

## Example — Add PRIMARY KEY

```sql
ALTER TABLE student
ADD PRIMARY KEY (rollno);
```

---

## Example — Add UNIQUE Constraint

```sql
ALTER TABLE student
ADD UNIQUE (email);
```

---

# 7. DROP CONSTRAINT 🚫

Used to remove constraints.

---

## Example

```sql
ALTER TABLE student
DROP PRIMARY KEY;
```

---

# Important Points 🚨

- ALTER changes table structure only
    
- Existing data may be affected
    
- Used after table creation
    

---

# Important Viva Questions 🎤

### Q1. What is ALTER command used for?

To modify existing table structure.

---

### Q2. Which language category does ALTER belong to?

DDL.

---

### Q3. Which keyword adds new column?

`ADD`

---

### Q4. Which keyword removes column?

`DROP COLUMN`

---

### Q5. Which keyword changes datatype?

`MODIFY`

---

### Q6. Can ALTER rename columns?

Yes.

---

### Q7. Can ALTER rename tables?

Yes.

---

### Q8. Does ALTER modify data?

Mostly structure only.

---

### Q9. Can constraints be added using ALTER?

Yes.

---

### Q10. Which command removes PRIMARY KEY?

`DROP PRIMARY KEY`

---

# Common Exam Queries 💀

## Add column

```sql
ALTER TABLE employee
ADD salary INT;
```

---

## Modify datatype

```sql
ALTER TABLE employee
MODIFY name VARCHAR(100);
```

---

## Delete column

```sql
ALTER TABLE employee
DROP COLUMN age;
```

---

## Rename column

```sql
ALTER TABLE employee
RENAME COLUMN name TO emp_name;
```

---

# Teacher Trap Questions 😭

### “What happens to existing data when adding column?”

Existing rows get NULL/default values.

---

### “Can ALTER recover dropped column?”

Usually no unless backup exists.

---

### “Difference between ALTER and UPDATE?”

|ALTER|UPDATE|
|---|---|
|Changes structure|Changes data|

---

# Quick Revision ⚡

|Operation|Purpose|
|---|---|
|ADD|Add column|
|MODIFY|Change datatype|
|DROP COLUMN|Remove column|
|RENAME COLUMN|Rename column|
|RENAME TO|Rename table|

[[DBMS Lab Experiments]]