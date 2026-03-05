### Definition

The **CAP Theorem** states that a **distributed database system cannot guarantee all three properties (Consistency, Availability, and Partition Tolerance) at the same time**.

A system can provide **only two out of the three properties** simultaneously.

CAP stands for:

- [[#1. Consistency (C)|C – Consistency]]
- [[#2. Availability (A)|A – Availability]]
- [[#3. Partition Tolerance (P)|P – Partition Tolerance]]

This theorem was proposed by **Eric Brewer**.

---

# 1. Consistency (C)

### Definition

Consistency means **all nodes in the distributed system return the same latest data at the same time**.

When a user reads data, they always get the **most recent updated value**.

### Example

Suppose a user has **₹500 in a bank account**.
He spends **₹200**, so the balance should become **₹300**.

![[Pasted image 20260305234050.png]]
If the system is consistent:
- DB1 → Balance = **300**
- DB2 → Balance = **300**

But if the update reaches **only one database**:
- DB1 → **300**
- DB2 → **500**

Now the system shows **different values**, so it becomes **inconsistent**.
👉 So **consistency means every node shows the same updated value**.

---

# 2. Availability (A)

### Definition

Availability means **every request to the system receives a response**, even if some nodes fail.

The system remains **operational at all times**.

### Example
Imagine a **YouTube creator** with **1000 subscribers**.
A user from another location wants to **subscribe**.
Even if the system uses **different database servers**, the subscription should still work.

![[Pasted image 20260305234239.png]]
After subscribing:
Subscribers → **1001**

If the system refuses the request because servers are not synchronized, then **availability is lost**.

👉 Availability means **the system always responds to user requests**.

---

# 3. Partition Tolerance (P)

### Definition

Partition tolerance means the system **continues working even when there is a communication failure between nodes**.

This happens when the network **splits into partitions** and servers cannot communicate with each other.

### Example

1. If one data center cannot communicate with another due to network failure, the system should still function.

2. Suppose two database servers store subscriber data:
- **DB1**
- **DB2**

A **network failure happens**, so DB1 cannot communicate with DB2.

Even though the connection is broken, the system **still allows users to check subscriber count using stored replica data**.

So the system keeps running despite the **network partition**.

![[Pasted image 20260305234529.png]]

👉 Partition tolerance means **system keeps working during network failures**.



---


Module : [[DBMS Module 3]]