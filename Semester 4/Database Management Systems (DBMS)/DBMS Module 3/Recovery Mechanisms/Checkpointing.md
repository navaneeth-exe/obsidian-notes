### 📌 Definition

**Checkpointing** is a recovery technique used to **reduce recovery time** by periodically saving the current state of the database.

👉 Instead of scanning the entire log after a crash, we start from the **last checkpoint**

---

# 🧠 Why Checkpointing?

Without checkpoint:

- System scans **full log** 😵 (slow AF)

With checkpoint:

- Scan only from **last checkpoint** ⚡

👉 Faster recovery = less headache

---

# ⚙️ What happens during a Checkpoint?

### Steps:

1. 🚫 **Stop accepting new transactions** (temporarily)
2. ⏳ Wait for active transactions to reach safe state
3. 💾 Flush all modified buffers to disk
4. 📝 Write checkpoint record in log:

```
<CHECKPOINT {T1, T2, ...}>
```
5. ▶️ Resume normal execution

---

# 🧾 Types of Checkpointing

---

## 1️⃣ Sharp Checkpoint (Quiescent)

### 📌 Definition

- Stops ALL transactions completely

### ⚙️ Working

- No active transactions during checkpoint

### ✅ Advantage

- Very simple

### ❌ Disadvantage

- Poor performance (system pause 😬)

---

## 2️⃣ Fuzzy Checkpoint (Non-Quiescent)

### 📌 Definition

- Does NOT stop transactions

### ⚙️ Working

- Some transactions continue running
- Only partial info saved

### ✅ Advantage

- Better performance

### ❌ Disadvantage

- More complex recovery

---

# 🔄 Recovery using Checkpoint

### After Crash:

1. Find **last checkpoint** in log
2. Identify:
    - ✅ Committed transactions → REDO
    - ❌ Uncommitted transactions → UNDO

---

# 🧠 Key Idea

👉 Checkpoint acts like a **save game 🎮**  
You don’t restart from level 1, only from last save 😎

---

# ✅ Advantages

- Reduces recovery time
- Limits log scanning
- Improves system performance during recovery

---

# ❌ Disadvantages

- Overhead during checkpoint
- Slight delay in system

---

# 🧾 Important Exam Points 🔥

- Checkpoint record:

```
<CHECKPOINT {active transactions}>
```

- Works with **log-based recovery**
- Used with **UNDO + REDO systems**