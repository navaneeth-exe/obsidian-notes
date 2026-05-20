Operators are used in SQL to perform:

- comparisons
    
- logical operations
    
- filtering conditions
    

Mostly used with:

- `WHERE`
    
- `SELECT`
    
- `UPDATE`
    
- `DELETE`
    

---

# 1. Arithmetic Operators 🔢

Used for mathematical operations.

|Operator|Meaning|
|---|---|
|+|Addition|
|-|Subtraction|
|*|Multiplication|
|/|Division|
|%|Modulus|

---

## Example

```sql
SELECT marks + 5
FROM student;
```

Adds 5 to marks.

---

# 2. Comparison (Relational) Operators 🎯

Used to compare values.

|Operator|Meaning|
|---|---|
|=|Equal to|
|!= or <>|Not equal|
|>|Greater than|
|<|Less than|
|>=|Greater than or equal|
|<=|Less than or equal|

---

## Examples

```sql
SELECT *
FROM student
WHERE marks > 80;
```

---

```sql
SELECT *
FROM student
WHERE dept = 'CSE';
```

---

# 3. Logical Operators 🧠

Used to combine conditions.

|Operator|Meaning|
|---|---|
|AND|Both conditions true|
|OR|Any one condition true|
|NOT|Opposite condition|

---

## AND Example

```sql
SELECT *
FROM student
WHERE dept='CSE' AND marks > 80;
```

---

## OR Example

```sql
SELECT *
FROM student
WHERE dept='CSE' OR dept='ECE';
```

---

## NOT Example

```sql
SELECT *
FROM student
WHERE NOT dept='CSE';
```

---

# 4. Special Operators ✨

---

## LIKE

Pattern matching.

```sql
SELECT *
FROM student
WHERE name LIKE 'A%';
```

Names starting with A.

---

## BETWEEN

Checks range.

```sql
SELECT *
FROM student
WHERE marks BETWEEN 70 AND 90;
```

---

## IN

Checks multiple values.

```sql
SELECT *
FROM student
WHERE dept IN ('CSE', 'ECE');
```

---

## IS NULL

Checks NULL values.

```sql
SELECT *
FROM student
WHERE marks IS NULL;
```

---

# Important Viva Questions 🎤

### Q1. What are SQL operators?

Symbols used to perform operations on data.

---

### Q2. Which operator checks equality?

`=`

---

### Q3. Difference between AND and OR?

|AND|OR|
|---|---|
|Both conditions true|Any one true|

---

### Q4. Which operator is used for pattern matching?

`LIKE`

---

### Q5. What does `%` represent in LIKE?

Multiple characters.

---

### Q6. Which operator checks range of values?

`BETWEEN`

---

### Q7. Which operator checks multiple values?

`IN`

---

### Q8. How do you check NULL values?

`IS NULL`

---

### Q9. Which operator means “not equal to”?

`!=` or `<>`

---

### Q10. What is NOT operator used for?

To reverse a condition.

---

# Most Important Operator Combo 🚨

|Operator|Use|
|---|---|
|=|Equality|
|>|Greater than|
|AND|Combine conditions|
|OR|Alternative conditions|
|LIKE|Pattern matching|
|BETWEEN|Range|
|IN|Multiple values|

---

# Teacher Trap Question 😭

### “Can we use = NULL ?”

❌ Wrong

Correct:

```sql
IS NULL
```

Because NULL is not a normal value.

---

# Quick Revision ⚡

|Type|Operators|
|---|---|
|Arithmetic|+ - * / %|
|Comparison|= > < >= <= !=|
|Logical|AND OR NOT|
|Special|LIKE IN BETWEEN IS NULL|




[[DBMS Lab Experiments]]