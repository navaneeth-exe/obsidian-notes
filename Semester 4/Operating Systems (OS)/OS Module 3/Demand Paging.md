### Definition

**Demand Paging** is a virtual memory technique in which **pages of a process are loaded into main memory only when they are required for execution**. Instead of loading the entire program into RAM at the start, the operating system loads pages **on demand**.

This improves memory utilization and allows programs larger than the available RAM to run.

---
## Basic Idea

A process is divided into **pages** and stored on disk (backing store).

When the CPU needs a page:
- If the page is already in RAM → execution continues. 
- If the page is not in RAM → a **page fault occurs**, and the OS loads the required page from disk.

Thus, **only necessary pages are brought into memory**.

---

## Steps in Demand Paging

1. **CPU requests a page** during program execution.
2. **Page table is checked** to see if the page is in memory.
3. If the page is **present**, execution continues.
4. If the page is **not present**, a **page fault** occurs.
5. The operating system **locates the required page on disk**.
6. A **free frame** in RAM is found.
7. The required page is **loaded from disk into the frame**.
8. **Page table is updated**.
9. The process **restarts the instruction** that caused the fault.

This mechanism ensures that memory is used efficiently.

---

## Advantages of Demand Paging

1. **Efficient memory usage**  
    Only required pages are loaded.
    
2. **Faster program start-up**  
    Entire program need not be loaded initially.
    
3. **Supports large programs**  
    Programs larger than physical memory can run.
    
4. **Allows higher multiprogramming**  
    More processes can stay in memory simultaneously.
    

---

## Disadvantages of Demand Paging

1. **Page fault overhead**  
    Disk access is slower than RAM.
    
2. **Performance reduction if faults are frequent**
    
3. **May lead to thrashing**  
    Excessive page faults cause heavy swapping.
    

---

## Hardware Support Required

Demand paging requires:
- **Page table**
- **Valid/invalid bit** (to check if page is in memory)
- **Backing store (disk)**
- **Memory Management Unit (MMU)**


Module : [[OS Module 3]]