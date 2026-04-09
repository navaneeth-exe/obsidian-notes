## ✅ **Definition**

A **cascading rollback schedule** is a schedule in which **failure of one transaction causes multiple other dependent transactions to roll back**.

👉 Simple meaning:  
If one transaction fails → all transactions that used its data also fail 😵

---

## 🔑 **Why it Happens**

- A transaction reads **uncommitted data** (dirty read)
- If the original transaction aborts → all dependent ones must also abort

---

## 📌 **Example**

```
T1: W(X)  
T2: R(X)  
T3: R(X)  
A1
```

👉 Explanation:

- T1 writes X (not committed)
- T2 reads X
- T3 also reads X
- Now T1 aborts ❌

👉 Result:

- T2 must rollback
- T3 must rollback

💀 Chain reaction = Cascading rollback

---

## 🔥 **Key Points**

- Occurs due to **dirty reads**
- Causes **multiple rollbacks**
- Wastes time and resources
- Not desirable in DBMS ❌