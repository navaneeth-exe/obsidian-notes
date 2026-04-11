## **Definition**

Segmentation is a memory management technique in which a process is divided into **variable-sized logical segments** such as code, data, and stack, and each segment is stored separately in physical memory.

---

## **Concept**

- A program is not a single block → it has logical parts:
    - Code
    - Data
    - Stack
- OS divides memory accordingly into **segments**
- Each segment is managed separately using **base and limit values**

---

## **Logical Address Format**

👉 **< Segment Number , Offset >**

- Segment Number → identifies the segment
- Offset → position inside that segment

---

## **Segment Table**

|Segment No|Base|Limit|
|---|---|---|
|0 (Code)|1000|400|
|1 (Data)|2000|300|
|2 (Stack)|3000|200|

---

## **Address Translation (Working)**

![[Pasted image 20260412022201.png|489]]

### Steps:

1. CPU generates **(Segment Number, Offset)**
2. Check:
    - If `Offset < Limit` → valid ✅
    - Else → **Trap (Segmentation Fault)** 🚫
3. If valid:
    
```
    Physical Address = Base + Offset
```
    

---

## **Example**

### Given:

Segment Table:

- Segment 0 → Base = 1000, Limit = 400
- Segment 1 → Base = 2000, Limit = 300

---

### ✅ Case 1: Valid Address

Logical Address = **(0, 150)**

- Check → 150 < 400 ✔️
- Physical Address = 1000 + 150 = **1150**

👉 Valid memory access

---

### ❌ Case 2: Invalid Address

Logical Address = **(1, 350)**

- Check → 350 < 300 ❌  
    👉 **Segmentation Fault (Trap to OS)**

---

## **Key Features**

- Variable-sized segments
- Logical division of memory
- Each segment has its own **base and limit**
- Supports protection and sharing

---

## **Advantages**

- Matches program structure
- Provides memory protection
- Allows sharing of segments

---

## **Disadvantages**

- External fragmentation
- Allocation is complex
- Slower than simple schemes

---

## **Important Points (Write for marks)**

- Logical address = **Segment Number + Offset**
- Uses **Segment Table**
- Translation = **Base + Offset**
- Invalid access → **Trap**
- Causes **external fragmentation**

---

## **One-Line Conclusion**

👉 _Segmentation divides memory into logical segments and translates addresses using base and limit registers with protection checks._