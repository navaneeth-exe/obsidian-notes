**BASE** properties are used in **NoSQL and distributed databases**.  
They are an **alternative to ACID properties** and focus on **availability and scalability instead of strict consistency**.

BASE stands for:

- **B – [[#1. Basically Available|Basically Available]]**
- **A – [[#2. Soft State|Soft State]]**
- **S – [[#2. Soft State|Eventual Consistency]]**

---

# 1. Basically Available

### Definition

The system **guarantees availability of data**, even if some parts of the system fail.

This means the system **always responds to requests**, but the response may not always contain the **most recent data**.

### Example

In large distributed systems like social media platforms:
- The system still responds to users
- But some data might be slightly outdated.

---

# 2. Soft State

### Definition

The **state of the system may change over time**, even without new input.

This happens because **data updates propagate gradually across distributed systems**.

### Example

If a user updates a profile picture, some servers may still show the **old picture for a short time** until synchronization happens.

---

# 3. Eventual Consistency

### Definition

The database will **eventually become consistent after some time**, once all updates are propagated across the system.

This means **all nodes will have the same data eventually**.

### Example

In distributed systems like **Amazon or social media platforms**, updates may take time to reflect everywhere, but eventually **all systems show the same data**.