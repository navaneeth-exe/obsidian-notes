## ✅ **Definition**

Serializability is a concept used to ensure that the **concurrent execution of transactions produces the same result as some serial execution** of those transactions.

👉 In simple words:  
Even if transactions run together, the result should look like they ran **one by one**.

---

## 🧠 **Why Serializability is Needed**

- Non-serial schedules can cause **inconsistency**
- Serializability ensures **correctness + concurrency**
- It is the **basis of concurrency control**

---

# 🔥 **Types of Serializability**

---

# 1️⃣ **Conflict Serializability (MOST IMPORTANT ⭐)**

---

## ✅ **Definition**

A schedule is said to be **conflict serializable** if it can be converted into a serial schedule by **swapping non-conflicting operations**.

---

## 🔹 **Conflict Operations**

Two operations conflict if:

1. They belong to **different transactions**
2. They access the **same data item**
3. At least one is a **write operation**

👉 Types:

- Read–Write (RW)
- Write–Read (WR)
- Write–Write (WW)

---

## 🔹 **Testing (Precedence Graph Method)**

### Steps:

1. Create a node for each transaction
2. Draw edge **Ti → Tj** if Ti’s operation occurs before a conflicting operation of Tj
3. Check graph:

👉 If **NO cycle** → Serializable ✅  
👉 If **cycle exists** → NOT Serializable ❌

---

## 📌 Example:

```
R1(A) → R2(A) → W1(A) → W2(A)
```

Conflicts:

- R1(A) before W2(A) → T1 → T2
- R2(A) before W1(A) → T2 → T1

👉 Cycle exists → ❌ Not serializable

---

# 2️⃣ **View Serializability**

---

## ✅ **Definition**

A schedule is **view serializable** if it produces the **same result as a serial schedule** based on:

---

## 🔹 Conditions:

1. **Initial Read** must be same
2. **Read-from relation** must be same
3. **Final Write** must be same


---
# ✍️ **Example for View Serializability**

---

## ✅ **Given Schedule S**

```
T1: R1(X), W1(X)    
T2: R2(X), W2(X)  
  
Schedule S:  
R1(X) → R2(X) → W1(X) → W2(X
```
---

## 🔍 **Check View Serializability**

We check **3 conditions**:

---

### 1️⃣ **Initial Read**

👉 Who reads the initial value of X?

- R1(X) reads initial value of X  
    ✔ Same as serial order T1 → T2

---

### 2️⃣ **Read-from Relationship**

👉 R2(X) reads value written by whom?

- R2(X) reads **initial value** (since W1(X) happens later)

✔ Same in serial order T1 → T2

---

### 3️⃣ **Final Write**

👉 Who does the final write on X?

- W2(X) is last → T2

✔ Same as serial order T1 → T2

---

## ✅ **Conclusion**

Since all three conditions are satisfied,  
👉 The schedule is **view serializable**

👉 Equivalent serial order:

```
T1 → T2
```
