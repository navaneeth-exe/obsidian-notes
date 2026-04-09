## **Definition**

A **Process Control Block (PCB)** is a data structure maintained by the operating system that stores **all information about a process** required for its execution and management.

---

## **Explanation**

- Every process has its own PCB.
- It acts like a **process identity card** 📇 for the OS.
- The OS uses PCB to:
    - Track process state
    - Manage scheduling
    - Perform context switching


---
![[Pasted image 20260410020856.png]]

---

## **Components of PCB**

### **1. Process Identification**

- Process ID (PID)
- Unique identifier for each process

---

### **2. Process State**

- Current state of the process:
    - New, Ready, Running, Waiting, Terminated

---

### **3. Program Counter (PC)**

- Stores the address of the **next instruction** to execute

---

### **4. CPU Registers**

- Includes:
    - General purpose registers
    - Stack pointer
    - Status registers

---

### **5. CPU Scheduling Information**

- Priority of process
- Scheduling queue pointers
- Time slice, etc.

---

### **6. Memory Management Information**

- Base and limit registers
- Page tables / segment tables

---

### **7. Accounting Information**

- CPU time used
- Process creation time
- User ID, job ID

---

### **8. I/O Status Information**

- List of I/O devices allocated
- Open files
- I/O requests

---

## 🔄 Role of PCB in Context Switching

- When CPU switches from one process to another:
    1. Current process state is saved in its PCB
    2. Next process state is loaded from its PCB
- This is called **context switching**

---

## **Key Points (Write for Extra Marks)**

- PCB is stored in **main memory (kernel space)**
- It is created when a process is created and deleted when process terminates
- It enables **multi-tasking** in OS
- Without PCB, process management is impossible