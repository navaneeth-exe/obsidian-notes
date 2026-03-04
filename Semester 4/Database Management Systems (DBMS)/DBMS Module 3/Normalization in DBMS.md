### Definition

**Normalization** is the process of **organizing data in a database to reduce redundancy (duplicate data) and eliminate [[Anomalies]]** by dividing large tables into smaller related tables.

In simple terms:  
Normalization helps to **store data efficiently and avoid data repetition**.

---
## Why Normalization is Needed

Normalization helps to:

- **Remove duplicate data**
- **Improve data consistency**
- **Reduce storage space**
- **Avoid [[Anomalies]] (insert, update, delete problems)**
- **Maintain data integrity**

---

## Example (Without Normalization)

Student Table

|Student_ID|Student_Name|Course|Instructor|
|---|---|---|---|
|101|Rahul|DBMS|Anil|
|101|Rahul|OS|Meera|
|102|Anu|DBMS|Anil|

Problems:

- **Student name repeats**
- **Instructor repeats**
- Waste of storage
- Hard to update

---

## After Normalization

### Student Table

|Student_ID|Student_Name|
|---|---|
|101|Rahul|
|102|Anu|

### Course Table

|Course|Instructor|
|---|---|
|DBMS|Anil|
|OS|Meera|

### Enrollment Table

|Student_ID|Course|
|---|---|
|101|DBMS|
|101|OS|
|102|DBMS|

Now:

- No duplication
- Data stored efficiently
---


## Types of Normal Forms in DBMS

**Normal Forms** are the **stages of normalization** used to organize a database and reduce redundancy.

The main normal forms are:

- **1NF (First Normal Form)**
- **2NF (Second Normal Form)**
- **3NF (Third Normal Form)**
- **BCNF (Boyce–Codd Normal Form)**

---

# 1. First Normal Form (1NF)

### Definition

A relation is in **1NF** if:
1. Each attribute contains **atomic (single) values**
2. There are **no repeating groups**
3. Each record can be uniquely identified

### Example (Not in 1NF)

|Student_ID|Name|Courses|
|---|---|---|
|101|Rahul|DBMS, OS|

Problem:  
**Courses column has multiple values**

### After Converting to 1NF

|Student_ID|Name|Course|
|---|---|---|
|101|Rahul|DBMS|
|101|Rahul|OS|

Now each field contains **only one value**.

---

# 2. Second Normal Form (2NF)

### Definition

A relation is in **2NF** if:
1. It is already in **1NF**
2. There is **no partial dependency**

Meaning:  
Non-key attributes must depend on the **entire primary key**, not just part of it.

### Example

```
| Student_ID | Course_ID | Student_Name | Grade |
```

Primary Key: **(Student_ID, Course_ID)**

Functional Dependency:

$$
Student_ID → Student_Name
$$

Problem:  
Student_Name depends only on **Student_ID**, not the full key.

### Solution

Split into two tables.

Student Table

```
| Student_ID | Student_Name |
```

Enrollment Table

```
| Student_ID | Course_ID | Grade |
```
Now **partial dependency is removed**.

---

# 3. Third Normal Form (3NF)

### Definition

A relation is in **3NF** if:
1. It is in **2NF**
2. There is **no transitive dependency**

Meaning:  
A non-key attribute should **not depend on another non-key attribute**.

### Example

```
| Student_ID | Dept_ID | Dept_Name |
```

Functional Dependencies:

$$
Student_ID → Dept_ID  
$$
$$
Dept_ID → Dept_Name
$$

Here:

$$
Student_ID → Dept_Name
$$

This is **transitive dependency**.

### Solution

Split tables.

Student Table

```
| Student_ID | Dept_ID |
```

Department Table

```
| Dept_ID | Dept_Name |
```

Now the dependency problem is removed.

---

# 4. Boyce–Codd Normal Form (BCNF)

### Definition

A relation is in **BCNF** if:

For every functional dependency:

$$
X → Y
$$

**X must be a super key**.

BCNF is a **stronger version of 3NF**.

### Example

```
| Student | Course | Instructor |
```

Dependencies:

```
(Student, Course) → Instructor  
Instructor → Course
```

Problem:  
**Instructor is not a super key**, so it violates BCNF.

Solution:  
Split the relation into smaller tables.