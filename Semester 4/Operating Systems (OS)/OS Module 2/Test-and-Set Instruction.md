## **Definition**

**Test-and-Set** is an **atomic hardware instruction** used for synchronization that **tests a memory location and sets it to a new value in one indivisible step**.

👉 Used to implement **mutual exclusion (locks)**

---

## **Concept**

- Multiple processes try to enter **critical section**
- We use a shared variable:

lock = 0   // free  
lock = 1   // busy

👉 Test-and-Set ensures:

> Only ONE process can set it from 0 → 1 at a time

 ---
 
## **Pseudo Code**

### Test-and-Set Function:

```
boolean TestAndSet(boolean *target) {  
    boolean old = *target;  
    *target = true;  
    return old;  
}
```

---

## **Using Test-and-Set (Lock Implementation)**

```
while (TestAndSet(&lock))  
    ; // busy wait  
  
// critical section  
  
lock = false;

```
---

## **Working**

1. Process calls **TestAndSet(lock)**
2. If lock = false:
    - It becomes true
    - Process enters critical section
3. If lock = true:
    - Process keeps waiting (**busy waiting**)

---

## **Key Properties**

- **Atomic operation** (cannot be interrupted)
- Ensures **mutual exclusion**
- Used for **spinlocks**

---

## **Advantages**

- Simple to implement
- Works at hardware level
- Guarantees mutual exclusion

---

## **Disadvantages**

- **Busy waiting (CPU waste)** 😬
- Not efficient for long waiting
- Can cause starvation

---

## **Important Points (WRITE FOR MARKS)**

- Test-and-Set is atomic
- Used for synchronization
- Implements locks
- Causes busy waiting