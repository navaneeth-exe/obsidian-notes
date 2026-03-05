Module : [[DBMS Module 3]]

**ACID properties** are a set of rules that ensure **reliable and consistent execution of transactions** in a database system.

ACID stands for:
- **A – Atomicity**
- **C – Consistency**
- **I – Isolation**
- **D – Durability**

These properties make sure that **database transactions are processed correctly even in case of failures**.

---

# 1. Atomicity

### Definition

**Atomicity** means a transaction is treated as a **single unit of work**.
It must be **completed entirely or not executed at all**.

### Example

Bank transfer of ₹1000:

1. Deduct ₹1000 from Account A
2. Add ₹1000 to Account B

If step 2 fails, the system **rolls back step 1**.
So the transaction is **all or nothing**.

---

# 2. Consistency

### Definition

**Consistency** ensures that a transaction **takes the database from one valid state to another valid state**.

It maintains **database rules and constraints**.

### Example

If the total money in two accounts is ₹5000 before the transaction, it must **remain ₹5000 after the transaction**.

No data integrity rules should be violated.

---

# 3. Isolation

### Definition

**Isolation** ensures that **multiple transactions executing at the same time do not interfere with each other**.

Each transaction behaves **as if it is the only transaction running in the system**.

### Example

Two users withdrawing money simultaneously should not cause **incorrect balances**.

Transactions are executed **independently**.

---

# 4. Durability

### Definition

**Durability** ensures that once a transaction is **committed**, the changes are **permanently stored in the database**, even if a system failure occurs.

### Example

After a successful bank transfer, the updated balance will **remain saved even if the system crashes or power fails**.
