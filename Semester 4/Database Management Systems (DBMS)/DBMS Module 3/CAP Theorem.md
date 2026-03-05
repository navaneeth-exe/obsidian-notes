### Definition

The **CAP Theorem** states that a **distributed database system cannot guarantee all three properties (Consistency, Availability, and Partition Tolerance) at the same time**.

A system can provide **only two out of the three properties** simultaneously.

CAP stands for:

- **[[#1. Consistency (C)]]**
- **[[A – Availability]]**
- **P – Partition Tolerance**

This theorem was proposed by **Eric Brewer**.

---

# 1. Consistency (C)

### Definition

Consistency means **all nodes in the distributed system return the same latest data at the same time**.

When a user reads data, they always get the **most recent updated value**.