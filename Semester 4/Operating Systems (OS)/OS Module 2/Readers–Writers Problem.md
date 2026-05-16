## **Definition**

The **Readers–Writers Problem** is a synchronization problem where:

- Multiple **readers** can read a shared resource simultaneously
- But **writers** require **exclusive access**

---

## **Problem**

- If a writer is writing → no reader or writer should access
- If readers are reading → multiple readers allowed
- Need to avoid:
    - **Race conditions**
    - **Data inconsistency**

---

## **Types (important concept)**

- **Reader-priority** → readers don’t wait
- **Writer-priority** → writers don’t starve

👉 Here we use **reader-priority solution (most common)**

# **Solution using Semaphores**

## **Variables**

```
int readcount = 0;  
semaphore mutex = 1;   // protects readcount  
semaphore wrt = 1;     // controls access to resource
```

---

## **Reader Process**

```
wait(mutex);  
readcount++;  
if (readcount == 1)  
    wait(wrt);   // first reader blocks writers  
signal(mutex);  
  
// Reading section  
  
wait(mutex);  
readcount--;  
if (readcount == 0)  
    signal(wrt); // last reader allows writers  
signal(mutex);
```

---

## **Writer Process**

```
wait(wrt);  
  
// Writing section  
  
signal(wrt);
```

---

## **Explanation**

- `mutex` → protects `readcount`
- `wrt` → ensures mutual exclusion for writers
- First reader locks writers
- Last reader releases writers

---

# **Explanation of Readers–Writers Solution (Semaphore)**

We are using:

```
int readcount = 0;  
semaphore mutex = 1;  
semaphore wrt = 1;
```

---

## **What each variable does**

- **readcount** → number of readers currently reading
- **mutex** → protects `readcount` (so no race condition)
- **wrt** → controls access to shared data (writers OR readers)

---

# **Reader Explanation**

### 🔹 Step 1: Entry section

```
wait(mutex);  
readcount++;  
if (readcount == 1)  
    wait(wrt);  
signal(mutex);
```

👉 What happens:

- First reader comes:
    - `readcount = 1`
    - It locks `wrt` → blocks writers ❌
- Next readers:
    - Just increase `readcount`
    - No need to lock again

💡 Meaning:

> First reader stops writers, others just join reading

---

### 🔹 Step 2: Reading section

👉 Multiple readers can read at the same time ✅

---

### 🔹 Step 3: Exit section

```
wait(mutex);  
readcount--;  
if (readcount == 0)  
    signal(wrt);  
signal(mutex);
```

👉 What happens:

- Readers leave one by one
- Last reader:
    - `readcount = 0`
    - Releases `wrt` → writers allowed

💡 Meaning:

> Last reader lets writers enter

---

# **Writer Explanation**

```
wait(wrt);  
  
// Writing  
  
signal(wrt);
```

👉 What happens:

- Writer waits until:
    - No reader is reading
    - No other writer is writing

👉 Once inside:

- Exclusive access (only writer)
---

# **Problem in this Solution**

👉 **Writer Starvation**

- If readers keep coming → writer may never get chance