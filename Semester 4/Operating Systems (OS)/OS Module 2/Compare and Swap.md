## **Definition**

**Compare-and-Swap (CAS)** is an **atomic hardware instruction** that compares a memory location with an expected value and **updates it only if they are equal**.
## **Concept**

👉 It works like:

> “If value == expected → update it, else do nothing”

This prevents multiple processes from modifying the same data simultaneously.

## **Pseudo Code**

```
int CompareAndSwap(int *value, int expected, int new) {  
    int old = *value;  
    if (*value == expected)  
        *value = new;  
    return old;  
}

```
---

## **Using CAS (Lock Implementation)**

```
while (CompareAndSwap(&lock, 0, 1) != 0)  
    ; // busy wait  
  
// critical section  
  
lock = 0;
```

---

## **Working**

1. Process checks if `lock == 0`
2. If yes → sets it to 1 → enters critical section
3. If no → keeps trying (**busy waiting**)

---

## **Key Properties**

- **Atomic** operation
- No interruption possible
- Used in **lock-free algorithms**

---

## **Advantages**

- More powerful than Test-and-Set
- Avoids unnecessary updates
- Used in modern synchronization

---

## **Disadvantages**

- Still causes **busy waiting** 😬
- Can lead to starvation