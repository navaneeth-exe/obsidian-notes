## **1. Direct Mapped Cache**

### **Replacement**

- Each memory block maps to **only one fixed cache line**
- When a new block comes, it **directly replaces the existing block**

### **Key Point**

- **No replacement algorithm needed**
- Replacement is **automatic**

---

## **2. Set-Associative Cache**

### **Replacement**

- Cache is divided into **sets**
- A block can be placed in **any line within the set**
- If set is full → one block must be replaced

### **Replacement Policies Used**

- **LRU (Least Recently Used)**
- **FIFO (First In First Out)**
- **Random replacement**
### **Policy Used: LRU (Most Important 🔥)**

- **Least Recently Used (LRU)**:
    - Block **not used recently is replaced**
    - Based on **temporal locality** (recent data likely used again)

### **Working (from example)**

- Suppose blocks map to same set
- When new block comes:
    - Check **use bits**
    - Block marked as **least recently used is replaced**

### **Advantages of LRU**

- Reduces cache misses
- Improves performance

---

## **3. Fully Associative Cache**

### **Replacement**

- A block can be placed in **any cache line**
- When cache is full → one block is replaced

### **Replacement Policies Used**

- **LRU**
- **FIFO**
- **Random**