Module : [[OS Module 3]]


# 1. Page Hit

### Definition

A **Page Hit** occurs when the page required by the CPU **is already present in the main memory (RAM)**.

### Working

1. CPU generates a **virtual address**.
2. The **page table** is checked.
3. If the page is marked **present/valid**, the page is in memory.
4. The memory access continues normally.


**Key Point**
No disk access is needed → **execution is fast**.

Example:
```
Page Table  
Page 0 → Frame 5  
Page 1 → Frame 2  
Page 2 → Frame 7  
  
CPU requests Page 1 → already in RAM → Page Hit
```


---

# 2. Page Fault

### Definition

A **page fault** occurs when a process tries to access a page that is **not currently present in the main memory (RAM)**. The required page is stored in secondary storage (disk), so the operating system must bring it into memory before the process can continue.

Page faults occur in systems that use **virtual memory with demand paging**.

## Steps in Page Fault Handling

When a page fault occurs, the operating system performs the following steps:

1. **Page Fault Trap**  
    The hardware detects that the required page is not in memory and generates a **page fault interrupt (trap)** to the operating system.
    
2. **Check Validity of Reference**  
    The OS checks whether the memory reference is **valid or invalid**.
    - If the reference is invalid → the process is terminated.
    - If valid → the OS continues the page fault handling.
        
3. **Locate Page on Disk**  
    The operating system finds the required page in the **backing store (secondary storage)**.
    
4. **Find a Free Frame**  
    The OS searches for a **free frame in main memory**.
    
5. **Page Replacement (if necessary)**  
    If no free frame is available, the OS selects a **victim page** using a page replacement algorithm such as:
    
    - FIFO
    - LRU
    - Optimal
6. **Load the Page into Memory**  
    The required page is **read from disk and loaded into the selected frame in RAM**.
    
7. **Update Page Table**  
    The page table entry is updated:
    - frame number is recorded
    - valid bit is set to **1**

8. **Restart the Interrupted Instruction**  
    The instruction that caused the page fault is **re-executed**, and the program continues normally.


![[Pasted image 20260307023047.png]]


---

## Page Fault Handling Flow (Diagram for Exam)

```
CPU requests a page  
        ↓  
Check page table  
        ↓  
Page in memory?  
   ↓         ↓  
 Yes        No  
(Page Hit)  Page Fault  
             ↓  
        Trap to OS  
             ↓  
      Locate page on disk  
             ↓  
      Find free frame  
             ↓  
     Replace page if needed  
             ↓  
      Load page into RAM  
             ↓  
     Update page table  
             ↓  
     Restart instruction
```