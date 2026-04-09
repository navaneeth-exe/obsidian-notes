### 📌 Definition

**Shadow Paging** is a recovery technique where the database maintains **two page tables**:

- **Shadow Page Table (old, stable copy)**
- **Current Page Table (working copy)**

👉 Instead of modifying data directly, the system **creates new copies of pages** and updates them.

---

# ⚙️ Basic Idea

👉 Original data is NEVER overwritten  
👉 All updates go to **new pages**  
👉 Old version stays safe = instant recovery 💥

---

# 🧠 Structure

- **Shadow Page Table**
    - Stored on disk
    - Never modified during transaction
- **Current Page Table**
    - Used during execution
    - Updated whenever changes happen

---

# 🔄 Working (Step-by-Step)

### 🟢 Before Transaction

- Both page tables point to same data pages

---

### 🟡 During Transaction

- When a page is modified:
    1. Create a **new copy of that page**
    2. Update current page table to point to new page
    3. Shadow page table remains unchanged

---

### 🔵 On Commit

- Replace **shadow page table** with **current page table**

👉 Boom 💥 changes become permanent

---

### 🔴 On Crash

- Discard current page table
- Use shadow page table

👉 Database automatically restored (no redo/undo needed 😎)

---

# 🧾 Example (Simple)

Initial:

```
Shadow Table → A → Page1
```

After update:

```
Current Table → A → Page2 (new)  
Shadow Table → A → Page1 (old)
```

---

# ✅ Advantages

- No need for **UNDO/REDO**
- Fast recovery (just switch tables)
- No cascading rollback
- Simple conceptually

---

# ❌ Disadvantages

- Requires **extra storage**
- Page copying overhead
- Fragmentation problem
- Not suitable for large databases
- Hard to implement with concurrent transactions