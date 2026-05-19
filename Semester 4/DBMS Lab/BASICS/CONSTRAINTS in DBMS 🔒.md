
Constraints are rules applied on table columns to maintain:

- data accuracy
    
- consistency
    
- integrity
    

Basically DBMS saying:  
“bro don’t insert dumb data here” 😭

---

# Common Constraints 📚

|Constraint|Purpose|
|---|---|
|PRIMARY KEY|Unique identification|
|FOREIGN KEY|Link tables|
|NOT NULL|Prevent empty values|
|UNIQUE|No duplicate values|
|CHECK|Restrict values|
|DEFAULT|Assign default value|

---

# 1. PRIMARY KEY 🔑

Uniquely identifies each row.

```sql
CREATE TABLE Student (
    rollno INT PRIMARY KEY,
    name VARCHAR(30)
);
```

✅ No duplicates  
✅ No NULL values

---

# 2. FOREIGN KEY 🔗

Creates relationship between tables.

```sql
CREATE TABLE Orders (
    orderid INT PRIMARY KEY,
    cid INT,
    FOREIGN KEY (cid)
    REFERENCES Customer(cid)
);
```

---

# 3. NOT NULL 🚫

Prevents empty values.

```sql
CREATE TABLE Student (
    name VARCHAR(30) NOT NULL
);
```

---

## Invalid Insert ❌

```sql
INSERT INTO Student VALUES (NULL);
```

Error occurs.

---

# 4. UNIQUE ✨

Prevents duplicate values.

```sql
CREATE TABLE Employee (
    email VARCHAR(50) UNIQUE
);
```

---

## Allowed

|email|
|---|
|[abc@gmail.com](mailto:abc@gmail.com)|
|[xyz@gmail.com](mailto:xyz@gmail.com)|

---

## Not Allowed ❌

|email|
|---|
|[abc@gmail.com](mailto:abc@gmail.com)|
|[abc@gmail.com](mailto:abc@gmail.com)|

Duplicate = error 💀

---

# 5. CHECK ✅

Restricts values based on condition.

```sql
CREATE TABLE Student (
    age INT CHECK(age >= 18)
);
```

---

## What it does

Only allows age 18 or above.

---

# 6. DEFAULT 🎯

Assigns automatic value if no value given.

```sql
CREATE TABLE Employee (
    city VARCHAR(20) DEFAULT 'Palakkad'
);
```

---

## Insert

```sql
INSERT INTO Employee VALUES ();
```

---

## Output

|city|
|---|
|Palakkad|

---

# Full Example Table 💀

```sql
CREATE TABLE Student (
    rollno INT PRIMARY KEY,
    name VARCHAR(30) NOT NULL,
    email VARCHAR(50) UNIQUE,
    age INT CHECK(age >= 18),
    city VARCHAR(20) DEFAULT 'Palakkad'
);
```

---

# Important Viva Questions 🎤

### Q1. What are constraints?

Rules applied on columns to maintain data integrity.

---

### Q2. Why are constraints used?

To prevent invalid data entry.

---

### Q3. Which constraint prevents NULL values?

`NOT NULL`

---

### Q4. Which constraint prevents duplicate values?

`UNIQUE`

---

### Q5. Difference between PRIMARY KEY and UNIQUE?

|PRIMARY KEY|UNIQUE|
|---|---|
|No NULL allowed|NULL allowed|
|Only one per table|Multiple allowed|

---

### Q6. Which constraint creates relationship between tables?

`FOREIGN KEY`

---

### Q7. What is CHECK constraint?

Restricts values based on condition.

---

### Q8. What is DEFAULT constraint?

Provides automatic value.

---

### Q9. Can PRIMARY KEY contain NULL?

No.

---

### Q10. Can UNIQUE contain NULL?

Yes (usually one NULL depending on DBMS).

---

# Most Important Constraint Combo 🚨

|Constraint|Main Use|
|---|---|
|PRIMARY KEY|Unique row|
|FOREIGN KEY|Table relation|
|NOT NULL|Mandatory value|
|UNIQUE|No duplicates|
|CHECK|Condition|
|DEFAULT|Auto value|

---

# Teacher Trap Questions 😭

### “Difference between UNIQUE and PRIMARY KEY?”

PRIMARY KEY:

- unique
    
- no NULL
    

UNIQUE:

- unique
    
- NULL allowed
    

---

### “Can a table have multiple UNIQUE constraints?”

Yes.

---

### “Can CHECK validate salary > 0?”

Yes.

```sql
salary INT CHECK(salary > 0)
```