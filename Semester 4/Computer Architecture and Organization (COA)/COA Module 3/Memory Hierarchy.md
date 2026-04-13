## **Definition**

Memory hierarchy is a technique used to **organize different types of memory into levels** to reduce the gap between **fast CPU and slow memory**, improving performance.

---

## **Need for Memory Hierarchy**

- CPU is **very fast**, memory is **comparatively slow**
- Causes **speed gap** → CPU waits for memory
- Hierarchy helps **bridge this gap**

---

## **Levels of Memory Hierarchy**

### **1. Registers**

- Located inside CPU
- **Fastest memory**
- Very small size
- Stores immediate data for execution

---

### **2. Cache Memory (L1, L2, L3)**

- Located close to CPU
- Faster than main memory
- Stores **frequently used data**
- Reduces access time

---

### **3. Main Memory (RAM)**

- Stores currently executing programs
- Moderate speed and size
- Accessed when data not in cache

---

### **4. Secondary Memory**

- Hard disk / SSD
- Very large storage
- Slowest memory
- Stores permanent data


---

## **Working**

1. CPU first checks **cache memory**
2. If data found → **cache hit (fast access)**
3. If not → check **main memory**
4. If still not found → fetch from **secondary memory**
5. Frequently used data is stored in **cache for future use**

---
## **Concept of Locality**

### **Temporal Locality**

- Recently used data is likely to be used again

### **Spatial Locality**

- Nearby data locations are likely to be accessed

👉 This is why cache works efficiently

---

## **Significance**

### **1. Improves Performance**

- Reduces memory access time
- Faster data access

---

### **2. Bridges Speed Gap**

- Reduces delay between CPU and memory

---

### **3. Cost Optimization**

- Fast memory = expensive
- Slow memory = cheap
- Combination gives **best cost-performance**

---

### **4. Efficient Data Access**

- Frequently used data is quickly available

---

## **Key Points (Write this 💯)**

- Organizes memory into **levels based on speed & size**
- Uses **cache to store frequently used data**
- Based on **locality principle**
- Reduces **CPU waiting time**