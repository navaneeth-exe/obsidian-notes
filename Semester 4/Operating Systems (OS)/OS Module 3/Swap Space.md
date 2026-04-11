## **Definition**

**Swap Space** is a portion of secondary storage (disk) used by the operating system to **temporarily store pages or processes that are not currently in main memory (RAM)**.

---

## **Concept**

- RAM is limited 😬
- OS moves inactive pages/processes to disk
- Frees RAM for active processes

👉 This process is called:

- **Swapping** (process level)
- **Paging to disk** (page level)

💡 Gives illusion of **large memory (virtual memory)**

---

## **Why Swap Space is Needed**

- To support **multiprogramming**
- To handle **large programs**
- To improve **memory utilization**
- To avoid **out-of-memory situations**

---

## **Working of Swap Space**

### Steps:

1. RAM becomes full
2. OS selects inactive pages/processes
3. Moves them to **swap space (disk)** → _swap out_
4. When needed → bring back to RAM → _swap in_

---

## **Types of Swapping**

### **1. Process Swapping**

- Entire process moved to disk
- Used in older systems

---

### **2. Page Swapping (Demand Paging)**

- Only required pages moved
- Used in modern systems

---

## **Swap Space Implementation**

### **1. Swap Partition**

- Separate disk partition
- Faster (no file system overhead)

---

### **2. Swap File**

- File inside file system
- Easier to manage

---

## **Advantages**

- Extends available memory
- Supports more processes
- Enables virtual memory
- Improves system flexibility

---

## **Disadvantages**

- Disk is slow 🐢
- Excessive swapping → **thrashing**
- Performance degradation