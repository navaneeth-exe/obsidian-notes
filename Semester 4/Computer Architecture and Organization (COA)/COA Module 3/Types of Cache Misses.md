## **1. Compulsory Miss (Cold Start Miss)**

### **Definition**

Occurs when a memory block is accessed **for the first time**, so it is **not present in cache**.

### **Reason**

- Cache is initially empty
- First access always causes a miss

### **Key Point**

- Cannot be avoided

---

## **2. Conflict Miss**

### **Definition**

Occurs when **multiple memory blocks map to the same cache location**, causing replacement even if cache has free space elsewhere.

### **Reason**

- Limited placement in **direct-mapped or set-associative cache**
- Blocks compete for same cache line

### **Key Point**

- Caused due to **mapping conflicts**

---

## **3. Capacity Miss**

### **Definition**

Occurs when the cache **cannot hold all required data**, so some blocks are replaced.

### **Reason**

- Cache size is too small
- Data exceeds cache capacity

### **Key Point**

- Happens even in fully associative cache

---

## **Final Points (Write this 💯)**

|Miss Type|Cause|
|---|---|
|Compulsory|First-time access|
|Conflict|Same cache location mapping|
|Capacity|Cache size insufficient|

---

# **How to Reduce Cache Miss (Exam Answer)**

Cache misses can be reduced using different techniques based on their type.

---

## **1. Reduce Compulsory Miss**

- Use **prefetching** (load data before it is needed)
- Use **larger cache block size** to bring more data at once

---

## **2. Reduce Conflict Miss**

- Use **set-associative or fully associative cache**
- Improve **mapping techniques**
- Use **better replacement algorithms**

---

## **3. Reduce Capacity Miss**

- Increase **cache size**
- Use **multi-level cache (L1, L2, L3)**
- Optimize programs for **better locality**

---

## **General Techniques**

- Improve **temporal locality** (reuse data)
- Improve **spatial locality** (access nearby data)
- Use efficient **cache replacement policies (LRU, FIFO)**

---

## **1. Cache Size**

- Increasing cache size reduces **capacity miss**
- More data can be stored → fewer replacements

---

## **2. Block Size**

- Increasing block size reduces **compulsory miss**
- More nearby data is fetched (spatial locality)
- But very large block size may increase miss penalty

---

## **3. Associativity**

- Higher associativity reduces **conflict miss**
- Allows multiple blocks to be placed in same set
- Example: Set-associative or fully associative cache

---

## **4. Other Techniques**

- **Prefetching** → reduces compulsory miss
- **Multi-level cache (L1, L2, L3)** → reduces capacity miss
- **Better replacement policies (LRU, FIFO)**