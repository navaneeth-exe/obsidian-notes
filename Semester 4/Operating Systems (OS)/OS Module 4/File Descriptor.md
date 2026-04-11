## **Definition**

A **File Descriptor** is a **non-negative integer** returned by the OS that uniquely identifies an **open file within a process**.

👉 It is used by the process to perform operations like:

- read
- write
- close

---

## **Concept**

- OS does **not give direct file access**
- Instead, it gives a **handle (FD)**

💡 Think:

> FD = “ID card for an open file” 




---
## **Standard File Descriptors**

| FD Number | Name   | Description               |
| --------- | ------ | ------------------------- |
| 0         | stdin  | Standard input (keyboard) |
| 1         | stdout | Standard output (screen)  |
| 2         | stderr | Standard error output     |


---

## **How It Works (Internally)**

### Flow:

1. Process calls `open()`
2. OS:
    - Creates entry in **system-wide open file table**
    - Creates entry in **process file descriptor table**
3. Returns **FD (integer)**

---

## **Three-Level Structure (VERY IMPORTANT)**

### **1. Per-Process File Descriptor Table**

- Stores:
    - FD number → pointer to open file

---

### **2. System-Wide Open File Table**

- Stores:
    - File offset (current position)
    - Access mode (read/write)
    - Reference count

---

### **3. Inode Table**

- Stores:
    - File metadata
    - Disk block locations