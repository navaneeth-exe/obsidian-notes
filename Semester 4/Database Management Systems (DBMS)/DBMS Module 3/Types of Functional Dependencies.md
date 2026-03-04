Module: [[DBMS Module 3]]  
Subject: [[Database Management Systems]]  
Semester: [[Semester 4]]
## 1. Trivial Functional Dependency

### Definition

A **trivial functional dependency** occurs when the attribute on the **right side is already a part of the left side**.

**Condition**

$$
Y⊆X
$$

If **X → Y** and **Y is a subset of X**, it is called **trivial dependency**.

### Example

Relation:

```
| Student_ID | Name | Course |
```

Functional Dependency:

$$
(Student_ID, Name) → Name
$$

Explanation:

- The attribute **Name** already exists in the left side.
- Therefore it is a **trivial dependency**.

### Key Point

Right side attribute is **already included in the left side**.

---

# 2. Non-Trivial Functional Dependency

### Definition

A **non-trivial functional dependency** occurs when the attribute on the **right side is not a subset of the left side**.

**Condition**

$$
Y⊈X
$$

### Example

```
| Student_ID | Name | Department |
```

Functional Dependency:

$$
Student_ID → Name
$$

Explanation:

- **Name** is not part of **Student_ID**.
- Therefore it is a **non-trivial dependency**.

### Key Point

Right side attribute **does not exist on the left side**.

---

# 3. Fully Functional Dependency

### Definition

A **fully functional dependency** occurs when an attribute depends on the **entire composite key**, not on any part of the key.

### Example

```
| Student_ID | Course_ID | Grade |
```

Primary Key: **(Student_ID, Course_ID)**

Functional Dependency:

$$
(Student_ID, Course_ID) → Grade
$$

Explanation:

- **Grade depends on both Student_ID and Course_ID together**
- If we remove one attribute, Grade cannot be determined.

### Key Point

Attribute depends on the **whole key**, not a part of it.

---

# 4. Partial Dependency

### Definition

A **partial dependency** occurs when a **non-prime attribute depends on only part of a composite key**.

### Example

```
| Student_ID | Course_ID | Student_Name |
```

Primary Key: **(Student_ID, Course_ID)**

Functional Dependency:

$$
Student_ID → Student_Name
$$

Explanation:

- **Student_Name depends only on Student_ID**
- It does not depend on the entire key.
    

### Key Point

Attribute depends on **only part of the key**.

⚠️ This causes **data redundancy** and is removed in **Second Normal Form (2NF)**.

---

# 5. Transitive Dependency

### Definition

A **transitive dependency** occurs when an attribute depends on another attribute **through a third attribute**.

If

```
A → B  
B → C

```
Then

```
A → C
```

This is called **transitive dependency**.

### Example

```
| Student_ID | Department_ID | Department_Name |
```

Functional Dependencies:

$$
Student_ID → Department_ID  
$$
$$
Department_ID → Department_Name
$$

Therefore:

$$
Student_ID → Department_Name
$$

Explanation:

- Department_Name depends on Department_ID
- Department_ID depends on Student_ID

So Department_Name **indirectly depends on Student_ID**.

### Key Point

Dependency occurs **through another attribute**.

⚠️ This is removed in **Third Normal Form (3NF)**.

---

# Quick Exam Summary Table

|Type|Meaning|
|---|---|
|Trivial|Right side attribute is part of left side|
|Non-Trivial|Right side attribute not part of left side|
|Fully Dependent|Depends on entire composite key|
|Partial Dependent|Depends on part of composite key|
|Transitive Dependent|Depends indirectly through another attribute|