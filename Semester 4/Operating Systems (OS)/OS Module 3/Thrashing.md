## **Definition**

**Thrashing** is a condition in which the system spends **more time swapping pages between RAM and disk than executing actual processes**.

---

## **Concept**

- System runs many processes → memory becomes insufficient
- Processes need pages not in RAM → **page faults increase**
- OS keeps swapping pages in and out

👉 CPU becomes idle, waiting for disk

💡 Result:

> System is busy… but doing nothing useful 😬

---

## **Working (What actually happens)**

![[Pasted image 20260412020322.png|595]]

### Steps:

1. Too many processes in memory
2. Each process gets fewer frames
3. Required pages not in memory
4. Frequent **page faults**
5. Continuous swapping (swap in/out)
6. CPU utilization drops

---

## **Key Indicator**

👉 **Very high page fault rate**

---

## **Graph Explanation (IMPORTANT)**

- Initially: more processes → CPU utilization increases
- After a point → memory overload  
    👉 CPU utilization **drops sharply**

👉 This drop = **Thrashing region**

---

## **Causes of Thrashing**

- High degree of multiprogramming
- Insufficient memory
- Poor page replacement algorithm
- Processes competing for frames

---

## **Effects**

- Low CPU utilization
- High disk activity
- System slowdown
- Poor performance

---

## **Solutions to Thrashing**

### **1. Reduce Degree of Multiprogramming**

- Remove some processes from memory

---

### **2. Working Set Model**

- Keep only required pages in memory

---

### **3. Page Fault Frequency (PFF) Control**

- Monitor page fault rate
- Allocate/deallocate frames accordingly

---

### **4. Use Better Page Replacement Algorithms**

- LRU, Optimal, etc.