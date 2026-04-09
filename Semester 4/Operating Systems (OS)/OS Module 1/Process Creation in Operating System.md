## **Definition**

Process creation is the mechanism by which an operating system loads a program into memory, initializes it, and prepares it for execution.

---

## **Steps Involved in Process Creation**

### **1. Loading Program into Memory**

- Programs are initially stored on **secondary storage** (disk/SSD).
- The OS reads the **executable file** and loads:
    - **Program code (text segment)**
    - **Static data (initialized variables)**
- These are placed into the process’s **address space in RAM**.

👉 Two types of loading:

- **Eager Loading**: Entire program loaded before execution.
- **Lazy Loading (Demand Paging)**: Only required parts are loaded during execution.

---

### **2. Memory Allocation for Stack**

- OS allocates memory for the **stack**.
- Used for:
    - Function calls
    - Local variables
    - Return addresses
- The OS initializes:
    - `argc` (argument count)
    - `argv[]` (argument vector)

![[Pasted image 20260410021555.png|266]]

---

### **3. Memory Allocation for Heap**

- OS creates initial **heap space**.
- Used for **dynamic memory allocation**:
    - `malloc()` → allocate memory
    - `free()` → deallocate memory
- Heap grows dynamically during execution.
![[Pasted image 20260410021630.png|225]]

---

### **4. I/O Initialization**

- OS sets up **Input/Output environment**.
- In UNIX systems, each process gets:
    - **0 → Standard Input**
    - **1 → Standard Output**
    - **2 → Standard Error**

👉 These are called **file descriptors** and allow interaction with devices like keyboard and screen.

---

### **5. Process Control Block (PCB) Creation**

- OS creates a **PCB** for the process containing:
    - Process ID (PID)
    - Process state
    - CPU registers
    - Memory information
    - Scheduling info

👉 PCB is essential for **process management and context switching**.

---

### **6. Setting Program Counter**

- OS sets the **Program Counter (PC)** to the entry point:
    - Usually the `main()` function

---

### **7. Starting Execution**

- OS transfers control to the process:
    - CPU starts executing instructions from `main()`
- The process moves to the **Ready → Running state**

---

## **Summary Flow**

```
Program on Disk  
      ↓  
Load Code & Data into Memory  
      ↓  
Allocate Stack & Heap  
      ↓  
Initialize I/O & PCB  
      ↓  
Set Program Counter to main()  
      ↓  
Start Execution
```