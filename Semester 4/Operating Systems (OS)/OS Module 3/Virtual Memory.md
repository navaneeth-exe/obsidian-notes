### Definition

**Virtual Memory** is a memory-management technique in which the operating system gives each process the illusion of having a large, contiguous main memory, even if the physical RAM is smaller. It does this by **keeping only part of a program in RAM and storing the rest on secondary storage (disk)**.

This allows programs larger than the available physical memory to execute.

---

## Basic Idea

Instead of loading the entire process into RAM:
1. The program is divided into **pages**.
2. Only **needed pages are loaded into main memory**.
3. Remaining pages stay on **disk (swap space / backing store)**.
4. When a required page is not in RAM, the OS loads it from disk.

This mechanism is called **Demand Paging**.