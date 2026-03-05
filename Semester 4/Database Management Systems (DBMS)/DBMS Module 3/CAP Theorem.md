### Definition

The **CAP Theorem** states that a **distributed database system cannot guarantee all three properties (Consistency, Availability, and Partition Tolerance) at the same time**.

A system can provide **only two out of the three properties** simultaneously.

CAP stands for:

- [[#1. Consistency (C)|C – Consistency]]
- **[[A – Availability]]**
- **P – Partition Tolerance**

This theorem was proposed by **Eric Brewer**.

---

# 1. Consistency (C)

### Definition

Consistency means **all nodes in the distributed system return the same latest data at the same time**.

When a user reads data, they always get the **most recent updated value**.

Example
Suppose a user has **₹500 in a bank account**.

He spends **₹200**, so the balance should become **₹300**.

If the system is consistent:

- DB1 → Balance = **300**
    
- DB2 → Balance = **300**
    

But if the update reaches **only one database**:

- DB1 → **300**
    
- DB2 → **500**
    

Now the system shows **different values**, so it becomes **inconsistent**.

CAP THEORM

👉 So **consistency means every node shows the same updated value**.