## ✅ **Definition**

A **recoverable schedule** is a schedule in which a transaction commits **only after all transactions whose data it has read have committed**.

👉 Simple meaning:  
If **T2 depends on T1**, then **T1 must commit before T2 commits**

---

## 🔑 **Key Condition**

If:

```
T2 reads data written by T1
```
Then:

```
Commit(T1) must happen before Commit(T2)
```

---

## 📌 **Example (Recoverable Schedule)**

```
T1: W(X)  
T2: R(X)  
C1  
C2
```

👉 Explanation:

- T2 reads X written by T1
- T1 commits before T2  
    ✔ Safe → Recoverable

---

## ❌ **Irrecoverable Schedule (for contrast)**

```
T1: W(X)  
T2: R(X)  
C2  
A1

```
👉 Problem:

- T2 commits before T1
- T1 aborts later

💀 T2 already used wrong data → cannot recover

---

## 🔥 **Why Recoverable Schedule is Important**

- Prevents **dirty commit**
- Ensures **safe recovery after failure**
- Maintains **database consistency**