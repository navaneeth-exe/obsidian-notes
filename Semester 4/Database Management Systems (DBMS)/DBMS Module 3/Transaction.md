Module: [[DBMS Module 3]]

### Definition

A **transaction** in DBMS is a **sequence of database operations (read/write) that are executed as a single logical unit of work**.

A transaction must **either complete fully or not execute at all**.

In simple terms:  
A transaction ensures **data consistency during database operations**.

---

## Example

Consider a **bank transfer**:

You transfer **₹1000 from Account A to Account B**.

Steps involved:

1. Deduct ₹1000 from **Account A**
2. Add ₹1000 to **Account B**

This entire process is **one transaction**.

If step 1 happens but step 2 fails, the system must **rollback**, otherwise money will disappear.

So the transaction must be **completed fully or cancelled completely**.


---

The main transaction operations are:

- **Read**
- **Write**
- **Commit**
- **Rollback**

# 1. Read Operation

### Definition

The **Read operation** retrieves the value of a data item from the database and stores it in a local variable.

### Syntax

```
Read(X)
```

Where **X** is a data item in the database.

### Example

If the balance of account **A** is stored in the database:

```
Read(A)
```

This operation reads the value of **A** into memory so the transaction can use or modify it.

---

# 2. Write Operation

### Definition

The **Write operation** updates the value of a data item in the database.

### Syntax

```
Write(X)
```

Where **X** is the updated data item.

### Example

A = A - 1000  
Write(A)

Here:
- The new value of **A** is written back to the database.
    

---

# 3. Commit Operation

### Definition

The **Commit operation** permanently saves all the changes made by a transaction into the database.

After a commit:

- The transaction **successfully completes**
    
- Changes **cannot be undone**
    

### Example

Commit

If a money transfer transaction is successful, the system performs **commit** to save the changes permanently.

---

# 4. Rollback Operation

### Definition

The **Rollback operation** cancels all changes made during a transaction and restores the database to its **previous state**.

Rollback is used when:

- An error occurs
    
- The transaction fails
    
- The system crashes
    

### Example

Rollback

If money is deducted from account **A** but cannot be added to account **B**, the system performs **rollback** so the balance returns to the original value.

---

# Example Transaction

Transfer ₹1000 from **Account A → Account B**

Read(A)  
A = A - 1000  
Write(A)  
  
Read(B)  
B = B + 1000  
Write(B)  
  
Commit

If any error occurs during the transaction:

Rollback

---

# Summary Table

|Operation|Meaning|
|---|---|
|Read|Retrieves data from database|
|Write|Updates data in database|
|Commit|Permanently saves changes|
|Rollback|Cancels transaction and restores old data|