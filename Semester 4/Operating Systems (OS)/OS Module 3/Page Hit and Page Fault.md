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