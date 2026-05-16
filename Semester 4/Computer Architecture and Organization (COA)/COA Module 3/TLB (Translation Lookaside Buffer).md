
REFER OS NOTES TOOO

REFER DIAGRAM IN PDF OR MS
## **Definition**

TLB is a **small, fast cache memory** that stores **recently used page table entries** to speed up address translation.

---

## **Need for TLB**

- Page table is stored in **main memory (slow)**
- Each access may require **2 memory accesses**
- TLB reduces this delay by storing **frequent translations**

---

## **Basic Concept**

- Located inside **MMU (Memory Management Unit)**
- Stores **VPN → PPN mappings**
- Works like a **cache for page table**

--- 
# **Address Translation using TLB (Exam Answer)**

## **Definition**

Address translation using TLB is the process of converting a **virtual address to a physical address** using the **Translation Lookaside Buffer (TLB)** for faster access.

---

## **Basic Concept**

- TLB stores **recent VPN → PPN mappings**
- It avoids accessing the page table every time
- Speeds up address translation

---

## **Steps in Address Translation using TLB**

1. CPU generates a **virtual address**
2. Split into:
    - **Virtual Page Number (VPN)**
    - **Page Offset**
3. Search **VPN in TLB**

---

### **Case 1: TLB Hit**

- VPN found in TLB
- Get **Physical Page Number (PPN)** directly
- Combine **PPN + Offset** → physical address
- Access main memory
- Only 1 memory access

---

### **Case 2: TLB Miss**

- VPN not found in TLB
- Access **page table in main memory**
- Get **PPN**
- Update TLB with new entry
- Form physical address and access memory