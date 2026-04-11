## **Definition**

A **Translation Lookaside Buffer (TLB)** is a **small, fast cache memory** that stores **recent page table entries** to speed up address translation.

---

## **Why TLB is Needed**

Without TLB:

- 1 memory access → page table
- 1 memory access → actual data

👉 Total = **2 memory accesses** (slow 😬)

💡 TLB reduces this to **1 access (most of the time)**

---

## **Concept**

- TLB stores:
    
    `(Virtual Page Number → Frame Number)`
    
- It is checked **before page table**

👉 Think:

> “Shortcut for page table lookup”

---

## **Working of TLB**

![[Pasted image 20260412021127.png|310]]


## **Steps (IMPORTANT)**

### Case 1: **TLB Hit** ✅

1. CPU generates Virtual Address (VPN + Offset)
2. VPN searched in **TLB**
3. Found → get Frame Number directly
4. Physical Address = Frame + Offset

👉 Only **1 memory access**

---

### Case 2: **TLB Miss** ❌

1. VPN not in TLB
2. Access **Page Table (in memory)**
3. Get Frame Number
4. Update TLB
5. Access actual data

👉 **2 memory accesses**

---

## **TLB Hit Ratio (VERY IMPORTANT)**

Let:

- Hit ratio = **h**
- Memory access time = **m**

👉 Effective Access Time (EAT):

EAT = h × (m) + (1 − h) × (2m)

👉 Simplified:

EAT = (2 − h) × m

----


# **TLB Entry (Complete Answer)**

## **Definition**

A **TLB Entry** is a single record inside the Translation Lookaside Buffer that stores a **cached virtual-to-physical address mapping** along with control information.

👉 It represents:

```
(VPN, ASID) → PFN + control bits
```

---

## **Structure of a TLB Entry**

![[Pasted image 20260412021301.png|375]]


## **Fields in TLB Entry (VERY IMPORTANT)**

### **1. VPN (Virtual Page Number / Tag)**

- Used for **searching the TLB**
- Compared with incoming address

---

### **2. PFN (Physical Frame Number)**

- Actual location in physical memory
- Used to form final physical address

---

### **3. Valid Bit**

- **1 → valid entry**
- **0 → invalid entry**

👉 If invalid → treated as **TLB miss**

---

### **4. Protection Bits**

- Define permissions:
    - Read
    - Write
    - Execute

👉 Prevents illegal memory access

---

### **5. Dirty Bit (Modified Bit)**

- Set when page is written
- Helps decide:
    - Write back to disk or not

---

### ⭐ **6. ASID (Address Space ID)** _(VERY IMPORTANT)_

- Identifies **which process the entry belongs to**

👉 So mapping becomes:

```
(VPN, ASID) → PFN
```

---

## **Why ASID is Needed**

👉 Problem:

- Two processes can have same VPN
- But different physical frames

👉 Solution:

- Use ASID to distinguish processes

---

## **Example (From PDF Concept)**

|VPN|PFN|ASID|
|---|---|---|
|6|88|P1|
|6|120|P2|

👉 Same VPN (6), different processes → no conflict ✅

---

## **How TLB Entry is Used**

1. CPU generates **(VPN, ASID)**
2. TLB searches entries:
    - If match → **TLB Hit**
    - Else → **TLB Miss**
3. On hit:
```
    Physical Address = PFN + Offset
```
    

---

## **Behavior During Context Switch**

From your PDF:

- OS loads:
    - **PTBR (Page Table Base Register)**
    - **ASID register**

👉 TLB is **NOT cleared**  
👉 Entries remain but are separated using ASID



---
## **Key Features**

- Very fast memory (usually associative memory)
- Stores recent page table entries
- Improves performance
- Small size

---

## **Advantages**

- Reduces memory access time 🚀
- Speeds up address translation
- Improves CPU performance

---

## **Disadvantages**

- Expensive hardware
- Limited size
- TLB miss still costly

---

## **Important Points (WRITE FOR MARKS)**

- TLB is a **cache for page table**
- Stores **VPN → PFN mapping**
- Hit → fast access
- Miss → normal paging
- Reduces **double memory access problem**