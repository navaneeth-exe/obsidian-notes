
`UNION` is used to combine results of two or more `SELECT` queries into a single result.

It combines rows vertically.

---

# Important Conditions 🚨

For `UNION` to work:

- Number of columns must be same
    
- Datatypes must be compatible
    
- Column order should match
    

---

# Syntax

```sql
SELECT column_name
FROM table1

UNION

SELECT column_name
FROM table2;
```

---

# Example Tables 🎓

## CSE Table

|name|
|---|
|Arun|
|Rahul|

---

## ECE Table

|name|
|---|
|Neha|
|Rahul|

---

# Example

```sql
SELECT name
FROM cse_students

UNION

SELECT name
FROM ece_students;
```

---

# Output

|name|
|---|
|Arun|
|Rahul|
|Neha|

---

# Important Point 🧠

Duplicate rows are removed automatically.

Here:  
`Rahul` appeared twice but shown once.

---

# UNION ALL 🔥

`UNION ALL` combines results without removing duplicates.

---

# Example

```sql
SELECT name
FROM cse_students

UNION ALL

SELECT name
FROM ece_students;
```

---

# Output

|name|
|---|
|Arun|
|Rahul|
|Neha|
|Rahul|

Duplicate preserved.

---

# UNION vs UNION ALL ⚔️

|UNION|UNION ALL|
|---|---|
|Removes duplicates|Keeps duplicates|
|Slower|Faster|

---

# Example with Different Tables 📚

## Employee Table

|empid|name|
|---|---|
|1|Arun|

---

## Manager Table

|mid|name|
|---|---|
|2|Neha|

---

# Query

```sql
SELECT name
FROM employee

UNION

SELECT name
FROM manager;
```

---

# Using ORDER BY with UNION 📈

```sql
SELECT name
FROM cse_students

UNION

SELECT name
FROM ece_students

ORDER BY name;
```

Sorting happens after combining results.

---

# Important Points 🚨

- Combines multiple SELECT outputs
    
- Duplicate rows removed in UNION
    
- Duplicate rows kept in UNION ALL
    
- Column count and datatype must match
    

---

# Important Viva Questions 🎤

### Q1. What is UNION used for?

To combine results of multiple SELECT queries.

---

### Q2. Does UNION remove duplicates?

Yes.

---

### Q3. Which operator keeps duplicates?

`UNION ALL`

---

### Q4. What conditions are required for UNION?

- Same number of columns
    
- Compatible datatypes
    

---

### Q5. Difference between UNION and UNION ALL?

|UNION|UNION ALL|
|---|---|
|Removes duplicates|Keeps duplicates|

---

### Q6. Can ORDER BY be used with UNION?

Yes.

---

### Q7. Does UNION combine tables permanently?

No. Only query results are combined.

---

# Common Exam Queries 💀

## Combine student names

```sql
SELECT name
FROM cse_students

UNION

SELECT name
FROM ece_students;
```

---

## Combine all including duplicates

```sql
SELECT name
FROM cse_students

UNION ALL

SELECT name
FROM ece_students;
```

---

# Teacher Trap Questions 😭

### “Can UNION combine tables with different column counts?”

No 💀

---

### “Which is faster: UNION or UNION ALL?”

`UNION ALL`

Because duplicate checking is skipped.

---

# Quick Revision ⚡

|Operator|Purpose|
|---|---|
|UNION|Combine results and remove duplicates|
|UNION ALL|Combine results and keep duplicates|

[[DBMS Lab Experiments]]