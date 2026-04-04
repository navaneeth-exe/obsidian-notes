A **semaphore** is a synchronization tool used to control access to the critical section and avoid race conditions.  
It is an integer variable accessed only through two atomic operations:

✅ **wait()** (also called P or down)  
✅ **signal()** (also called V or up)

---

## **1️⃣ wait() Operation**

**Purpose:**  
Decreases the semaphore value. If the resource is unavailable, the process is blocked.

**Implementation:**

```
wait(S)  
{  
    while (S <= 0)  
        ; // busy waiting (do nothing)  
    S = S - 1;  
}
```

**Explanation to write:**

- When a process calls wait(), it checks semaphore value.
- If S > 0 → it decrements S and enters critical section.
- If S ≤ 0 → process waits until resource is free.
- Ensures only limited processes enter critical section.

---

## **2️⃣ signal() Operation**

**Purpose:**  
Increases the semaphore value and wakes up a waiting process.

**Implementation:**

```
signal(S)  
{  
    S = S + 1;  
}
```
**Explanation to write:**

- signal() increments semaphore value.
- Indicates resource is released.
- Allows waiting process to enter critical section.