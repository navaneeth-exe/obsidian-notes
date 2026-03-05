Module: [[DBMS Module 3]]

### Definition

A **transaction** in DBMS is a **sequence of database operations (read/write) that are executed as a single logical unit of work**.

A transaction must **either complete fully or not execute at all**.

In simple terms:  
A transaction ensures **data consistency during database operations**.

---

## Example

Consider a **bank transfer**:

You transfer **₹1000 from Account A to Account B**.

Steps involved:

1. Deduct ₹1000 from **Account A**
2. Add ₹1000 to **Account B**

This entire process is **one transaction**.

If step 1 happens but step 2 fails, the system must **rollback**, otherwise money will disappear.

So the transaction must be **completed fully or cancelled completely**.

