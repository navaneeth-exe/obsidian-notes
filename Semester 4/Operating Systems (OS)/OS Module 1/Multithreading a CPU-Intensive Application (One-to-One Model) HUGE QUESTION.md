The system contains **dual-core processors with a total of 4 cores available for scheduling**. The application performs:

- Input only at the beginning
- CPU-intensive computation in the middle
- Output only at the end

The system uses a **one-to-one threading model**, where **each user thread maps to one kernel thread**. This allows multiple threads to run in parallel on different processors.

---

## **(a) Threads for Input and Output**

### **Answer:**

- **One thread for input**
- **One thread for output**

### **Explanation:**

The input operation occurs only once at program start and involves reading from a **single file**. File reading is generally sequential, meaning data must be read in order.

If multiple threads try to read the same file:

- They must share the file pointer
- Synchronization is required
- It can cause contention and race conditions
- No real performance improvement occurs

Similarly, output happens only once at the end and writes to a **single file**. Writing must also be sequential to maintain correct data order.

Creating multiple threads for I/O:

- Adds overhead
- Requires synchronization
- Does not increase speed

👉 Therefore, one thread each for input and output is optimal and efficient.

---

## **(b) Threads for CPU-Intensive Portion**

**Answer:**  
Four threads should be created.

**Explanation:**  
The middle part of the program is completely CPU-bound, meaning it mainly uses processor time and performs no I/O. Since the system has four processors, true parallelism is possible.

In the one-to-one threading model, each user thread maps to a kernel thread, and each kernel thread can run on a separate processor, allowing simultaneous execution.

	If fewer than four threads are used, some processors remain idle and CPU resources are wasted. If more than four threads are used, context switching increases and performance may decrease.

Hence, creating exactly four threads ensures full CPU utilization, true parallelism, and minimum overhead.