## **1. Write Through Policy**

### **Definition**

In write-through policy, whenever data is written, it is updated in **both cache and main memory simultaneously**.

### **Working**

- CPU writes data
- Data is written to cache
- SAME data is immediately written to disk/main memory
- Both copies stay consistent

### **Advantages**

- Ensures **data consistency**
- Simple to implement
- No data loss on crash

### **Disadvantages**

- Slower due to **frequent memory access**
- Increases memory traffic

---

## **2. Write Back (Copy Back) Policy**

### **Definition**

In write-back policy, data is written **only in cache** initially, and main memory is updated **only when the block is replaced**.

### **Working**

- CPU writes data
- Data is updated only in cache
- Cache marks that block as “dirty”
- Data is written to disk/memory only when:
    - Cache block is replaced 
    - Or explicitly flushed

### **Advantages**

- Faster performance
- Reduces memory traffic

### **Disadvantages**

- More complex
- Risk of inconsistency if not handled properly
- Risk of data loss

---

## **Key Points (Write this 💯)**

|Policy|Memory Update|
|---|---|
|Write Through|Cache + Memory immediately|
|Write Back|Cache first, Memory later|