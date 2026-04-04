## **Definition

Context switching is the process in which the operating system switches the CPU from one process to another by saving the state of the current process and loading the state of the next process. This allows multiple processes to share the CPU.

---
### **Why Context Switching is Needed 🎯**

- For **multitasking** (running many processes “at the same time”)
- To keep CPU busy while one process waits for I/O
- For **time-sharing systems** so each process gets CPU time
- To maintain system responsiveness
---

### **Why Context Switching is Needed 🎯**

- For **multitasking** (running many processes “at the same time”)
- To keep CPU busy while one process waits for I/O
- For **time-sharing systems** so each process gets CPU time
- To maintain system responsiveness

---
### **Advantages ✅**

- Enables multitasking
- Better CPU utilization
- Improves system responsiveness

---

### **Disadvantages ❌**

- Context switching takes time (overhead)
- Too many switches reduce performance
- No useful work done during switching

---

# **Steps Performed During a Context Switch**

## **1) Save the State of the Current Process**

The kernel first saves the current process’s context into its **Process Control Block (PCB)**.

This includes:

- Program Counter (PC)
- CPU registers
- Stack Pointer
- Process state (running, waiting, etc.)
- Memory-management info

👉 This ensures the process can resume later from the exact point it stopped.

---

## **2) Update Process State**

The kernel changes the state of the running process:

- From **Running → Ready** (if time slice expired)
- From **Running → Waiting** (if I/O request occurs)

---

## **3) Select a New Process**

The CPU scheduler selects another process from the **ready queue** based on scheduling algorithms like:

- FCFS
- Round Robin
- Priority Scheduling

---

## **4) Load the New Process State**

The kernel loads the saved context of the selected process from its PCB:

- Restores registers
- Restores program counter
- Restores memory info

👉 Now CPU is ready to run this process.

---

## **5) Switch Memory Mapping**

The kernel updates:

- Page tables
- Base and limit registers
- Virtual memory mappings

This ensures the new process gets its correct memory space.

---

## **6) Resume Execution**

The CPU starts executing the new process from where it was previously paused.