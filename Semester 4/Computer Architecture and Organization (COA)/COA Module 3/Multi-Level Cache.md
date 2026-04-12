## **Definition**

Multi-level cache is a memory organization technique where **more than one level of cache (L1, L2, etc.)** is used to **improve system performance and reduce memory access time**.

## **Need for Multilevel Cache**

- A **small cache** is very fast but stores less data
- A **large cache** stores more data but is slower
- So we use multiple levels to get **both speed and capacity**


- Processor is very fast, but main memory (DRAM) is slow
- Single large cache:
    - ↓ Miss rate but ↑ access time
- Small cache:
    - Fast but ↑ miss rate

👉 So we use **multiple cache levels to balance speed, cost, and size**



---

## **Levels of Multilevel Cache**

### **1. L1 Cache**

- Smallest and fastest
- Located closest to CPU
- Access time: ~1–2 cycles
- Higher miss rate

---

### **2. L2 Cache**

- Larger than L1
- Slower than L1 but faster than main memory
- Lower miss rate than L1
- Acts as backup for L1

📌 If L1 miss → check L2

---

### **3. L3 Cache (IMPORTANT ADDITION)**

- Larger than L2
- Slower than L1 and L2
- Shared among multiple cores
- Further reduces main memory access

👉 Acts as **last level cache before main memory**

---

## **Working of Multilevel Cache**

1. CPU checks **L1 cache**
2. If miss → check **L2 cache**
3. If miss → check **L3 cache**
4. If miss → fetch from **main memory**

👉 This hierarchical checking reduces access time significantly

---

## **Average Memory Access Time (AMAT)**

From your PDF (multi-level):

AMAT=tL1+MRL1×(tL2+MRL2×tMemory)AMAT = t_{L1} + MR_{L1} \times (t_{L2} + MR_{L2} \times t_{Memory})AMAT=tL1​+MRL1​×(tL2​+MRL2​×tMemory​)

Where:

- tL1t_{L1}tL1​ = L1 access time
- MRL1MR_{L1}MRL1​ = L1 miss rate
- tL2t_{L2}tL2​ = L2 access time
- MRL2MR_{L2}MRL2​ = L2 miss rate

📌 Lower AMAT = better performance


---
## **Advantages**

- Reduces average memory access time
- Improves CPU performance
- Minimizes expensive main memory access
- Efficient use of locality of reference

---

## **Disadvantages**

- Complex design
- Higher cost
- Cache coherence issues (multi-core systems)

---

## **Diagram (Draw This for Exam)**

CPU  
 ↓  
L1 Cache (Fastest, Smallest)  
 ↓  
L2 Cache  
 ↓  
L3 Cache (Shared)  
 ↓  
Main Memory

![[Pasted image 20260413021444.png|470]]