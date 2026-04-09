### 📌 Definition

**Log-based recovery** is a technique used to maintain database consistency using a **log file**, which records all transaction operations.

👉 Log is stored on **stable storage** (so it survives crashes)

---

### 🧠 Log Record Format

Each log entry contains:

```
<Ti, X, old_value, new_value>
```

- `Ti` → Transaction ID
- `X` → Data item
- `old_value` → Before update
- `new_value` → After update

Also:

```
<START Ti>  
<COMMIT Ti>  
<ABORT Ti>
```

---

# ⚡ Types of Log-Based Recovery

---

# 1️⃣ Deferred Update (Lazy Update)

### 📌 Definition

In **Deferred Update**, changes are **NOT written to database immediately**.  
They are applied **only after transaction commits**.

👉 Database stays unchanged until commit

---

### ⚙️ Working

- Updates stored only in **log**
- Actual DB updated **after commit**
- If crash happens → just ignore uncommitted transactions

---

### 🧠 Key Idea

👉 **No UNDO needed**, only REDO

---

### ✍️ Example Log

```
<START T1>  
<T1, A, 100, 200>  
<T1, B, 50, 70>  
<COMMIT T1>
```

---

### 🔄 Recovery Steps

- If **COMMIT present** → REDO transaction
- If **no COMMIT** → IGNORE transaction


---

### ✅ Advantages

- Simple recovery
- No risk of dirty data

### ❌ Disadvantages

- Updates delayed → slower execution

---

# 2️⃣ Immediate Update (Eager Update)

### 📌 Definition

In **Immediate Update**, changes are written to database **before commit**.

👉 Database can have **uncommitted data**

---

### ⚙️ Working

- Updates written immediately
- Log must store **old values** (for undo)
- Uses **Write-Ahead Logging (WAL)**:  
    👉 Log is written before actual data

---

### 🧠 Key Idea

👉 Needs both **UNDO + REDO**

---

### ✍️ Example Log

```
<START T1>  
<T1, A, 100, 200>  
<T1, B, 50, 70>  
<COMMIT T1>
```

---

### 🔄 Recovery Steps

- If **COMMIT present** → REDO
- If **no COMMIT** → UNDO

---

### ✅ Advantages

- Faster execution
- No need to wait for commit

### ❌ Disadvantages

- Complex recovery
- Risk of cascading rollback

---

# ⚠️ Write-Ahead Logging (IMPORTANT 🔥)

### 📌 Rule

👉 **Log must be written BEFORE database update**