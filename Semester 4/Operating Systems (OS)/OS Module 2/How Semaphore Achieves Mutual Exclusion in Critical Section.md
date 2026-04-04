## **Definition of Semaphore**

A semaphore is a synchronization tool used in operating systems to control access to shared resources by multiple processes. It is an integer variable accessed only through two atomic operations: **wait (P)** and **signal (V).**

---

# **Mutual Exclusion Using Semaphore**

To protect a critical section, a **binary semaphore (mutex)** is used.

👉 A binary semaphore has only two values: **0 and 1**

- **1 → resource free**
- **0 → resource in use**

---

## **Operations on Semaphore**

### **1. wait (P) operation**

- Decreases semaphore value by 1
- If value becomes 0 → process enters critical section
- If value < 0 → process is blocked and waits

```
wait(S){  
   while(S <= 0);  
   S = S - 1;  
}
```
---

### **2. signal (V) operation**

- Increases semaphore value by 1
- Wakes up a waiting process

```
signal(S){  
   S = S + 1;  
}
```

---

# **How It Ensures Mutual Exclusion**

1. Semaphore is initialized to **1**.
2. When a process wants to enter the critical section, it performs **wait(S)**.
3. If S = 1 → it becomes 0 and the process enters.
4. Any other process trying to enter must wait because S = 0.
5. When the process exits, it calls **signal(S)** making S = 1.
6. Now another process can enter.

👉 Thus, only **one process enters the critical section at a time.**

---

# **Semaphore Solution for Critical Section**

Assume a binary semaphore `S` initialized to **1**.

```
do {  
    wait(S);          // entry section  
  
    // Critical Section  
    // shared resource access  
  
    signal(S);        // exit section  
  
    // Remainder Section  
  
} while(true);
```

---

# **Correct Definition of Operations**

### **wait(S)**

```
wait(S){  
    while(S <= 0);   // busy wait  
    S = S - 1;  
}
```

### **signal(S)**

```
signal(S){  
    S = S + 1;  
}
```