## **Definition**

A **Page Table** is a data structure used by the operating system to **map logical pages to physical frames** during address translation.

## **Why Page Table is Needed**

- Pages are stored **anywhere in memory (non-contiguous)**
- OS must keep track of where each page is placed  
    👉 Page table acts as a **mapping directory**

---

## **Concept (From your PDF)**

- Virtual address space is divided into **pages**
- Physical memory is divided into **frames**
- **Page size = Frame size** (VERY IMPORTANT)

👉 OS stores mapping:

Virtual Page Number (VPN) → Physical Frame Number (PFN)

---

## **Address Translation Using Page Table**

![[Pasted image 20260412021636.png|383]]

### Steps:

1. CPU generates **Virtual Address (VA)**
2. VA is split into:
    - **Page Number (VPN)**
    - **Offset**
3. VPN → used to index **Page Table**
4. Get **Frame Number (PFN)**
5. Physical Address:
    
    `PA = PFN + Offset`
    

---

## **Address Splitting (IMPORTANT from PDF)**

From your PDF example (page ~9–11):

- Virtual Address Space = **64 Bytes**
- Page Size = **16 Bytes**

👉 Total pages = 64 / 16 = **4 pages**

👉 Bits required:

- VA = 6 bits (because 64 = 2⁶)
- Page Number = 2 bits (4 pages)
- Offset = 4 bits (16 = 2⁴)

👉 So:

```
VA = [ Page Number (2 bits) | Offset (4 bits) ]
```

---

## **Example (FROM YOUR PDF)**

### Given:

- VA = **21**
- Page Table:
    - Page 0 → Frame 3
    - Page 1 → Frame 7
    - Page 2 → Frame 5
    - Page 3 → Frame 2

---

### Step 1: Convert VA

21 = **010101 (binary)**

Split:

- Page Number = **01 (1)**
- Offset = **0101 (5)**

---

### Step 2: Page Table Lookup

Page 1 → Frame 7

---

### Step 3: Physical Address

PA = Frame 7 + Offset 5  
Binary: 111 + 0101 = 1110101  
Decimal = 117

👉 **Final Physical Address = 117**

---

# **Page Table Entry (PTE)**

## **Definition**

A **Page Table Entry (PTE)** is an entry in the page table that stores **information about a single virtual page**, including where it is located in physical memory and its status.

## **Fields in Page Table Entry (VERY IMPORTANT)**

### **1. Frame Number (PFN)**

- Stores the **physical frame address**
- Used to compute final physical address

---

### **2. Valid / Present Bit**

- **1 → Page is in memory**
- **0 → Page not in memory (invalid)**  
    👉 If 0 → **Page Fault occurs**

---

### **3. Protection Bits**

- Controls access permissions:
    - Read
    - Write
    - Execute  
        👉 Prevents illegal access

---

### **4. Reference Bit (Accessed Bit)**

- Set when page is accessed
- Used in **page replacement algorithms**

---

### **5. Dirty Bit (Modified Bit)**

- Set when page is modified
- Helps OS decide:
    - Save to disk or not

---

## **How PTE is Used in Address Translation**

1. CPU generates **Virtual Address (VPN + Offset)**
2. VPN → used to find **PTE**
3. From PTE:
    - Get **Frame Number**
    - Check **valid bit**
4. Physical Address = Frame + Offset

---

## **Example**

### Given:

PTE for Page 1:

- Frame = 7
- Valid = 1
- Dirty = 0

Logical Address = **(Page 1, Offset 20)**

👉 Physical Address:

```
PA = Frame 7 + Offset 20
```

👉 Page is valid → access allowed

---

### ❌ Invalid Case

If:

- Valid Bit = 0

👉 Result:  
➡️ **Page Fault (OS loads page into memory)**

---

## **Key Points (WRITE FOR MARKS)**

- Each page has one PTE
- Stores **frame number + control bits**
- Used during address translation
- Controls **protection + status**
- Helps in **page replacement**