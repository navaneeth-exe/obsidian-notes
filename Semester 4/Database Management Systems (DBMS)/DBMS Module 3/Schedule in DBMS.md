**Definition:**

A **schedule** is an ordering of operations (read, write, commit, abort) of multiple transactions such that the order of operations within each individual transaction is preserved.

👉 In simple terms:  
It represents how transactions are executed **concurrently in a database system**.

---

**Key Points:**

- A schedule involves **two or more transactions**
- Operations can be **interleaved**
- The internal order of each transaction must not change

---

**Example:**

```
T1: R(A), W(A)  
T2: R(B), W(B)  
  
Schedule S:  
R1(A) → W1(A) → R2(B) → W2(B)
```

---

# ✍️ **2. Types of Schedules**

---

# 🔹 **(a) Serial Schedule**

**Definition:**

A **serial schedule** is a schedule in which transactions are executed **one after another**, without any interleaving.

---

**Key Features:**

- No overlapping of transactions
- Simple and safe
- Always produces **correct results**
- No concurrency

---

**Example:**

```
T1: R(A) → W(A)  
T2: R(B) → W(B)  
  
Serial Schedule:  
R1(A) → W1(A) → R2(B) → W2(B)
```

---

**Advantages:**

- Easy to understand
- No inconsistency problems

**Disadvantages:**

- Poor performance
- Low resource utilization
- No parallel execution

---

# 🔹 **(b) Non-Serial (Concurrent) Schedule**

**Definition:**

A **non-serial (concurrent) schedule** is a schedule in which operations of multiple transactions are **interleaved** (executed simultaneously).

---

**Key Features:**

- Transactions execute simultaneously
- Improves system performance
- May cause data inconsistency if not controlled

---

**Example:**

```
R1(A) → R2(A) → W1(A) → W2(A)
```

---

**Advantages:**

- Better CPU utilization 🚀
- Faster execution

**Disadvantages:**

- Can cause problems like:
    - Lost update
    - Dirty read
    - Inconsistency