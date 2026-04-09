## ✅ **Definition**

A **cascadeless schedule** is a schedule in which **a transaction reads a data item only after the transaction that wrote it has committed**.

👉 Simple meaning:  
No transaction will read **uncommitted data**

---

## 🔑 **Condition**

If:

```
T2 reads data written by T1
```
Then:

```
Commit(T1) must happen BEFORE R2(X)
```

---

## 📌 **Example (Cascadeless Schedule)**

```
T1: W(X)  
C1  
T2: R(X)  
C2
```

👉 Explanation:

- T1 writes X and **commits first**
- Then T2 reads X  
    ✔ No dirty read  
    ✔ No rollback chain

---

## 🔥 **Why it is Important**

- Prevents **dirty reads**
- Avoids **cascading rollback**
- More reliable than recoverable schedule

---

## ❌ **What it Avoids**

👉 This will NOT happen:

```
T1: W(X)  
T2: R(X)  
A1
```

💀 Because T2 is not allowed to read before T1 commits