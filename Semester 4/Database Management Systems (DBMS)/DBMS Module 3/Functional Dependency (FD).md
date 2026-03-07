Module: [[DBMS Module 3]]
### Definition

A **Functional Dependency** in a relational database is a relationship between two sets of attributes where **one attribute uniquely determines another attribute**.

It is written as:

$$
X→Y
$$

Meaning:  
**Attribute X functionally determines attribute Y**

So if two rows have the **same value of X**, they **must have the same value of Y**.

### Example

Consider a **Student table**

| Student_ID | Name  | Department |
| ---------- | ----- | ---------- |
| 101        | Rahul | CSE        |
| 102        | Anu   | ECE        |
| 103        | Ravi  | CSE        |

Here:

```
Student_ID → Name  
Student_ID → Department
```

Explanation:
- Each **Student_ID** uniquely identifies a **Name**
- Each **Student_ID** uniquely identifies a **Department**

So **Student_ID functionally determines Name and Department**.


![[WhatsApp Image 2026-03-07 at 12.47.03 PM.jpeg]]

---
### [[Types of Functional Dependencies]]

1. Trivial 
2. Non-Trivial
3. Fully Dependent
4. Partial Dependent
5. Transitive Dependent