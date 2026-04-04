## **Definition**

A deadlock is a situation in an operating system where two or more processes are unable to proceed because each process is waiting for a resource that is held by another process. As a result, all the processes remain blocked forever.

👉 In short: _each process waits for others → none can continue._

---

## **Example**

Process P1 holds Resource R1 and waits for R2.  
Process P2 holds Resource R2 and waits for R1.  
Neither can proceed → **deadlock occurs.**

---

# **Necessary Conditions for Deadlock (Coffman Conditions)**

For a deadlock to occur, **all four conditions must be true at the same time.**

---

## **1. Mutual Exclusion**

At least one resource is non-shareable.  
Only one process can use it at a time.

✅ Example: Printer (only one process can use it)

---

## **2. Hold and Wait**

A process holds at least one resource and is waiting to acquire more resources held by other processes.

✅ Example: Holding printer, waiting for scanner

---

## **3. No Preemption**

Resources cannot be forcibly taken away from a process.  
They must be released voluntarily.

✅ Example: OS cannot take printer from a process until it finishes

---

## **4. Circular Wait**

A circular chain of processes exists where each process waits for a resource held by the next process.

✅ Example:  
P1 → waits for P2  
P2 → waits for P3  
P3 → waits for P1