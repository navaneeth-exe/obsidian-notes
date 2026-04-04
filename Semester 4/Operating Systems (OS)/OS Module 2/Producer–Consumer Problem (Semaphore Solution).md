## **Definition**

The Producer–Consumer problem is a classical synchronization problem in Operating Systems where:

- A **Producer** produces data (items)
- A **Consumer** consumes data
- Both share a **common buffer of fixed size**

The challenge is to synchronize them so that:

- Producer does not add data when buffer is full
- Consumer does not remove data when buffer is empty
- Only one process accesses the buffer at a time

---

# **Semaphore Solution**

Three semaphores are used:

- **S (Mutex)** = 1  
    → Controls mutual exclusion
- **E (Empty)** = n  
    → Counts empty slots in buffer
- **F (Full)** = 0  
    → Counts filled slots

---

# **Producer Process**

```
while(1)  
{  
    wait(E);  
    wait(S);  
  
    produce();  
  
    signal(S);  
    signal(F);  
}
```

### Meaning

- `wait(E)` → Check for empty slot
- `wait(S)` → Enter critical section
- `produce()` → Add item to buffer
- `signal(S)` → Leave critical section
- `signal(F)` → Increase full count

---

# **Consumer Process**

```
while(1)  
{  
    wait(F);  
    wait(S);  
  
    read();  
  
    signal(S);  
    signal(E);  
}
```
### Meaning

- `wait(F)` → Check for available item
- `wait(S)` → Enter critical section
- `read()` → Remove item from buffer
- `signal(S)` → Leave critical section
- `signal(E)` → Increase empty count
---

# **Producer Working (Step-by-step)**

```
wait(E);  
wait(S);  
produce();  
signal(S);  
signal(F);
```

### Explanation

✅ `wait(E)`

- Producer checks if empty space exists
- If no space → Producer waits

✅ `wait(S)`

- Locks the buffer
- No one else can access it

✅ `produce()`

- Item is added to buffer

✅ `signal(S)`

- Unlocks buffer

✅ `signal(F)`

- Increases full count (new item available)

---

# **Consumer Working (Step-by-step)**

```
wait(F);  
wait(S);  
read();  
signal(S);  
signal(E);
```

### Explanation

✅ `wait(F)`

- Consumer checks if item exists
- If buffer empty → waits

✅ `wait(S)`

- Locks buffer

✅ `read()`

- Removes item

✅ `signal(S)`

- Unlocks buffer

✅ `signal(E)`

- Increases empty count (space created)
---

## **How it works (Flow)**

### ✅ Initially

- Buffer is empty
- Empty slots = n
- Full slots = 0
- Mutex = 1

So:

- Producer can start producing
- Consumer must wait (nothing to consume)

---

### ✅ When Producer Runs

1. Producer checks if space is available.
2. If space exists, it enters the buffer safely.
3. It adds an item.
4. Now the number of full slots increases.
5. Consumer gets permission to consume.

👉 Result: Buffer slowly fills.

---

### ✅ When Consumer Runs

1. Consumer checks if items exist.
2. If items exist, it enters buffer safely.
3. It removes an item.
4. Now empty space increases.
5. Producer can produce again.

👉 Result: Buffer gets free space again.