## **Definition**

**Multiprogramming** is a technique used by an operating system where **multiple programs are kept in main memory at the same time**, and the CPU switches between them to maximize utilization.

---

## **Concept (Simple Explanation)**

- In a system, a single program doesn’t use the CPU all the time.
- Sometimes it waits (for I/O like disk, keyboard, etc.).
- Instead of wasting CPU time, the OS loads **multiple programs** into memory.
- When one program is waiting, **CPU is given to another program**.

👉 So CPU is _never idle_ — always doing something.

---

## **Key Idea**

💡 **Keep CPU busy all the time**

---

## **How it Works (Steps)**

1. Multiple jobs are loaded into memory.
2. OS selects one job and gives CPU.
3. If that job waits for I/O → CPU switches to another job.
4. This continues → efficient CPU usage.

---

## **Diagram (you can draw in exam)**

Memory:  
```
+------------------+  
| Program 1        |  
| Program 2        |  
| Program 3        |  
+------------------+  
```
CPU:  
Executes one at a time,  
switches when needed

![[Pasted image 20260412023039.png|409]]


---
## **Advantages**

- Better CPU utilization 💯
- Increased system throughput
- Reduced idle time
- Efficient resource usage

---

## **Disadvantages**

- Complex OS design
- Needs memory management
- CPU scheduling required
- Possibility of deadlocks

---

## **Important Points (for marks)**

- Multiple processes in memory
- CPU executes one process at a time
- Switch happens when process waits (mostly I/O)
- Improves CPU efficiency

---

## **Difference from Multitasking (1 line)**

- **Multiprogramming → maximize CPU usage**
- **Multitasking → improve user interaction (time-sharing)**