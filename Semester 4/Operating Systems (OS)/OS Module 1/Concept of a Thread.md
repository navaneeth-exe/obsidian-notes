## **Definition**

A **thread** is the smallest unit of execution within a process. It is also called a **lightweight process (LWP)** because it requires fewer resources than a process.

---

## **Explanation**

- A process can have **multiple threads**.
- All threads within a process **share the same memory space**, code, and resources.
- Each thread has its own:
    - Program Counter (PC)
    - Registers
    - Stack

---

## 📊 Diagram (Thread inside a Process)

![[Pasted image 20260410021201.png]]


---

## **Key Features of Threads**

- Threads share:
    - Code section
    - Data section
    - Files and resources
- Threads have separate:
    - Stack
    - Registers

---

## **Advantages of Threads**

1. **Responsiveness** – Improves application responsiveness
2. **Resource Sharing** – Easy communication between threads
3. **Economy** – Less overhead compared to processes
4. **Parallelism** – Multiple threads can run simultaneously on multi-core systems

---

## **Types of Threads**

1. **User-Level Threads**
    - Managed by user-level libraries
    - Faster but not handled by OS directly
2. **Kernel-Level Threads**
    - Managed by the operating system
    - Slower but more powerful