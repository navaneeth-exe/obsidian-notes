## ✅ **Definition**

A **strict schedule** is a schedule in which **a transaction is not allowed to read or write a data item until the transaction that last wrote that item has committed or aborted**.

👉 Simple meaning:  
No one touches a data item until the previous writer is done ✔

---

## 🔑 **Condition**

If:

```
T1 writes X
```

Then:

```
No other transaction can READ or WRITE X until T1 commits or aborts
```

---

## 📌 **Example (Strict Schedule)**

```
T1: W(X)  
C1  
T2: R(X)  
W2(X)  
C2
```

👉 Explanation:

- T1 writes X
- T2 waits ⏳
- After T1 commits → T2 reads/writes

✔ No dirty read  
✔ No dirty write  
✔ Fully safe

---

## 🔥 **Key Features**

- Prevents **dirty reads** ❌
- Prevents **dirty writes** ❌
- Avoids **cascading rollback** ❌
- Ensures **easy recovery** ✔

---

## 🧠 **Why Strict Schedule is Best**

👉 Compared to others:

- Recoverable → only safe commit
- Cascadeless → no dirty read
- **Strict → no dirty read + no dirty write (fully safe 💯)**