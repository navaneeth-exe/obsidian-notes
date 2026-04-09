## **Definition**

A **process** is a program in execution. During its lifetime, a process passes through different states, which are called **process states**.

---

## **Basic Process States (Five-State Model)**

![[Pasted image 20260410021315.png]]

### **1. New State**

- The process is being created.
- The operating system initializes necessary data structures like PCB.
- The process is not yet ready for execution.

---

### **2. Ready State**

- The process is loaded into main memory.
- It is waiting to be assigned to the CPU.
- All resources except CPU are available.

---

### **3. Running State**

- The process is currently executing on the CPU.
- Only one process can be in this state per processor core.

---

### **4. Waiting (Blocked) State**

- The process is waiting for an event such as I/O completion.
- It cannot execute until the event occurs.

---

### **5. Terminated (Exit) State**

- The process has completed execution.
- It is removed from the system by the OS.

---

## **Process State Transitions**

- **New → Ready** : Process is admitted by the OS
- **Ready → Running** : CPU scheduler allocates CPU
- **Running → Waiting** : Process requests I/O
- **Waiting → Ready** : I/O operation completes
- **Running → Ready** : Time slice expires (preemption)
- **Running → Terminated** : Execution finished

---

## **Additional Points**

- Each process is represented by a **Process Control Block (PCB)**.
- The OS uses **CPU scheduling** to manage process execution.
- **Context switching** occurs when CPU switches from one process to another.