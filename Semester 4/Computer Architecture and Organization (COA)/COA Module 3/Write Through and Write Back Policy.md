## **1. Write Through Policy**

### **Definition**

In write-through policy, whenever data is written, it is updated in **both cache and main memory simultaneously**.

### **Working**

- CPU writes data to cache
- At the same time, data is also written to main memory

### **Advantages**

- Ensures **data consistency**
- Simple to implement

### **Disadvantages**

- Slower due to **frequent memory access**
- Increases memory traffic

---

## **2. Write Back (Copy Back) Policy**

### **Definition**

In write-back policy, data is written **only in cache**, and main memory is updated **only when the block is replaced**.

### **Working**

- CPU writes data only to cache
- Modified block is marked (dirty bit)
- When block is replaced → updated in main memory

### **Advantages**

- Faster performance
- Reduces memory traffic

### **Disadvantages**

- More complex
- Risk of inconsistency if not handled properly

---

## **Key Points (Write this 💯)**

|Policy|Memory Update|
|---|---|
|Write Through|Cache + Memory immediately|
|Write Back|Cache first, Memory later|