

`IN` and `NOT IN` are used in SQL to check multiple values in a condition.

Instead of writing many `OR` conditions manually, we use `IN`.

---

# 1. IN Operator ✅

Used to match any value from a given list.

---

# Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name IN (value1, value2);
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
SELECT *
FROM student
WHERE dept IN ('CSE', 'ECE');
```

---

# Output

|rollno|name|dept|
|---|---|---|
|101|Arun|CSE|
|102|Neha|ECE|

---

# Equivalent OR Condition 💀

```sql
SELECT *
FROM student
WHERE dept='CSE' OR dept='ECE';
```

`IN` makes it shorter and cleaner.

---

# 2. NOT IN Operator ❌

Used to exclude values from a list.

---

# Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name NOT IN (value1, value2);
```

---

# Example

```sql
SELECT *
FROM student
WHERE dept NOT IN ('CSE', 'ECE');
```

---

# Output

|rollno|name|dept|
|---|---|---|
|103|Rahul|ME|

Only rows NOT matching CSE/ECE shown.

---

# Important Viva Questions 🎤

### Q1. What is IN operator used for?

To check multiple values in a condition.

---

### Q2. What is NOT IN used for?

To exclude specific values.

---

### Q3. Which operator can replace multiple OR conditions?

`IN`

---

### Q4. Difference between IN and NOT IN?

|IN|NOT IN|
|---|---|
|Includes matching values|Excludes matching values|

---

### Q5. Can IN be used with numbers and strings?

Yes.

---

# Common Exam Examples 💀

## Using IN

```sql
SELECT *
FROM employee
WHERE city IN ('Delhi', 'Mumbai');
```

---

## Using NOT IN

```sql
SELECT *
FROM employee
WHERE city NOT IN ('Delhi', 'Mumbai');
```

---

# Teacher Trap Question 😭

### “Is IN faster than multiple OR conditions?”

Usually cleaner and often optimized better by DBMS.

---

# Quick Revision ⚡

|Operator|Purpose|
|---|---|
|IN|Match values from list|
|NOT IN|Exclude values from list|