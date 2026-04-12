## **Definition**

A physical address is the **actual address in main memory (RAM)** used by the CPU to **access data after address translation**.

---

## **Basic Concept**

- CPU **does not directly use virtual address**
- Virtual address is converted into **physical address**
- Physical address is used to access **real memory location**

---

## **Structure of Physical Address**

A physical address is divided into two parts:

1. **Physical Page Number (PPN)**
    - Identifies the frame in main memory
2. **Page Offset**
    - Specifies the exact location within the page

👉 Physical Address = **PPN + Offset**

---

## **Working**

- CPU generates virtual address
- Address is translated using **page table / TLB**
- PPN is obtained
- Combined with offset to form **physical address**
- Memory is accessed using this address

---

## **Key Points (Write this 💯)**

- Used to access **main memory (RAM)**
- Obtained after **address translation**
- Consists of **PPN + offset**
- Offset remains same as virtual address