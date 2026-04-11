## **Definition**

Paging is a memory management technique where:

- Logical memory is divided into **fixed-size pages**
- Physical memory is divided into **fixed-size frames**
- Pages are mapped to frames using a **page table**

---

## **Concept**

- Process doesn’t need contiguous memory ❌
- OS splits memory into equal-sized blocks
- Pages can be placed **anywhere in RAM**

👉 This removes **external fragmentation** 😎

---

## **Key Idea**

💡 Divide → Map → Access

---

## **Logical Address Format**

👉 **< Page Number , Offset >**

- Page Number → used to find frame
- Offset → location inside page

---

## **Page Table**

|Page No|Frame No|
|---|---|
|0|5|
|1|2|
|2|8|
|3|1|

---

## **Address Translation (Working)**

![[Pasted image 20260412022028.png|441]]

### Steps:

1. CPU generates **(Page Number, Offset)**
2. Page Number → used to index **Page Table**
3. Get **Frame Number**
4. Physical Address:
    
```
    PA = Frame Number + Offset
```

---

## **Example (IMPORTANT)**

### Given:

- Page size = 100 bytes
- Page Table:

|Page|Frame|
|---|---|
|0|5|
|1|2|
|2|8|

---

### Logical Address = **250**

### Step 1: Find Page Number & Offset

Page Number = 250 / 100 = 2  
Offset = 250 % 100 = 50

---

### Step 2: Page Table Lookup

Page 2 → Frame 8

---

### Step 3: Physical Address

PA = (Frame × Page Size) + Offset  
   = (8 × 100) + 50  
   = 850

👉 Final Physical Address = **850**

---

## **Key Features**

- Fixed-size memory blocks
- Uses **Page Table**
- No need for contiguous allocation
- Efficient memory utilization

---

## **Advantages**

- No external fragmentation 🔥
- Simple allocation
- Supports virtual memory

---

## **Disadvantages**

- Internal fragmentation 😬
- Page table overhead
- Extra memory access (slower)

---

## **Important Points (EXAM GOLD)**

- Logical address = **Page No + Offset**
- Uses **Page Table**
- Pages map to frames
- Eliminates **external fragmentation**
- May cause **internal fragmentation**

---

## **One-Line Conclusion**

👉 _Paging divides memory into fixed-size pages and frames and maps them using a page table to allow non-contiguous allocation._