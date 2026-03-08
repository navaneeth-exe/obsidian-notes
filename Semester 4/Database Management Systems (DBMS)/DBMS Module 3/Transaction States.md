
Module : [[DBMS Module 3]]
# 1. Active State

### Definition

A transaction is in the **Active state** when it is **currently executing its operations**.
Operations like **read and write** are performed in this state.

### Example

```
Read(A)  
A = A - 100  
Write(A)
```

Here the transaction is **actively executing**.

If everything goes well, it moves to the **Partially Committed state**.

---

# 2. Partially Committed State

### Definition

A transaction enters the **Partially Committed state** after the **last statement of the transaction has been executed**, but the changes are **not yet permanently saved**.

At this stage the system checks whether the transaction can be safely committed.

### Example

All database operations are done, but the system has **not yet confirmed the commit**.

---

# 3. Committed State

### Definition

A transaction reaches the **Committed state** when **all its operations are successfully completed and the changes are permanently stored in the database**.

Once committed:

- Changes **cannot be undone**
- Data becomes **permanent**

### Example

```
Commit
```

Money transfer completed successfully.

---

# 4. Failed State

### Definition

A transaction enters the **Failed state** when it **cannot proceed further due to an error or system failure**.

Reasons may include:

- System crash
- Power failure
- Invalid data
- Hardware failure

At this stage the transaction cannot continue execution.

---

# 5. Aborted State

### Definition

When a transaction fails, the system performs a **rollback**, and the transaction moves to the **Aborted state**.

All changes made by the transaction are **undone**, and the database returns to its **previous consistent state**.

After aborting, the transaction may:

- Restart again  
    or
- Be completely terminated.

---

# Simple Flow of Transaction States

```
Active  
   ↓  
Partially Committed  
   ↓  
Committed
```

If error occurs:
```
Active  
   ↓  
Failed  
   ↓  
Aborted
```