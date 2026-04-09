## ✅ **Answer (Write this directly in exam)**

Concurrency means **multiple transactions execute at the same time**.  
If this concurrent execution is **not properly controlled**, it can lead to **inconsistency in the database**.

👉 Because:

- Transactions may **interfere with each other**
- They may **read or overwrite incomplete data**
- Order of execution becomes unpredictable

---

## 🔥 **Main Problems Caused by Concurrency**

---

# 1️⃣ **Lost Update Problem**

👉 One transaction’s update is **overwritten by another**

**Example:**

T1: Read(X=100) → X = X - 10 → Write(X=90)  
T2: Read(X=100) → X = X + 20 → Write(X=120)

👉 Final value becomes **120**,  
but correct value should be **110**

💀 T1 update lost

---

# 2️⃣ **Dirty Read (Temporary Update Problem)**

👉 A transaction reads **uncommitted data**

**Example:**

T1: Write(X=200)  (not committed)  
T2: Read(X=200)  
T1: Abort

👉 T2 used invalid data → wrong result ❌

---

# 3️⃣ **Unrepeatable Read Problem**

👉 Same data gives **different values** in same transaction

**Example:**

T1: Read(X=100)  
T2: Update X=150  
T1: Read(X=150)

👉 T1 gets different values 😵

---

# 4️⃣ **Incorrect Summary Problem**

👉 Aggregate operations give wrong result

**Example:**

- T1 calculates sum
- T2 updates values simultaneously

👉 Some values old, some new → wrong total ❌