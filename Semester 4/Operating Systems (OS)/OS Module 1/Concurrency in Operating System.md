## **Definition**

Concurrency is the ability of an operating system to **execute multiple processes or threads simultaneously or in overlapping time periods**.

---

## **Explanation**

- Multiple processes **progress at the same time**
- Execution may not be truly parallel (on single CPU) but appears simultaneous using **CPU scheduling**
- Achieved using:
    - **Multitasking**
    - **Multithreading**
    - **Multiprocessing**

---

## **Key Characteristics of Concurrency**

- **Interleaving Execution**: Processes take turns using CPU
- **Shared Resources**: Memory, files, I/O devices
- **Independent Processes**: May or may not interact
- **Non-deterministic Execution**: Order of execution may vary

---

## **Advantages of Concurrency**

1. **Improved CPU Utilization**
2. **Increased Throughput**
3. **Better Responsiveness**
4. **Efficient Resource Sharing**

---

## **Problems in Concurrency**

### **1. Race Condition**

- Occurs when multiple processes access shared data simultaneously
- Final result depends on execution order

---

### **2. Critical Section Problem**

- Section of code where shared resources are accessed
- Must ensure **mutual exclusion**

---

### **3. Deadlock**

- Two or more processes wait indefinitely for each other

---

### **4. Starvation**

- A process never gets CPU due to scheduling

---

## **Solutions to Concurrency Problems**

- **Mutex (Mutual Exclusion Locks)**
- **Semaphores**
- **Monitors**
- **Synchronization mechanisms**