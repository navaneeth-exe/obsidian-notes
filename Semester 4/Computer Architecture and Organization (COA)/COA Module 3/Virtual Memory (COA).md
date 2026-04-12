## **Definition**

Virtual memory is a memory management technique that allows a system to **use secondary storage (disk) as an extension of main memory**, giving the illusion of a **large memory space** even when RAM is limited.

---

## **Need for Virtual Memory**

- Programs may be **larger than available RAM**
- Entire program cannot be loaded at once
- Virtual memory allows execution by **loading only required parts**

---

## **Basic Concept**

- Program uses **virtual addresses**
- OS converts them into **physical addresses**
- Only required data is kept in RAM, rest stays on disk

---

## **Working**

1. Program is divided into **pages**
2. Only few pages are loaded into RAM initially
3. CPU generates **virtual address**
4. Address is converted to **physical address**
5. If required page is present → executed
6. If not → **page fault occurs**
7. OS loads required page from disk to RAM

---

## **Key Concepts**

- **Virtual Address Space** → Logical memory used by program
- **Paging** → Dividing memory into fixed-size pages
- **Page Fault** → When required page is not in RAM

---

## **Advantages**

- Allows execution of **large programs**
- Efficient memory usage
- Supports multiprogramming

---

## **Key Points (Write this 💯)**

- Uses **disk as extension of RAM**
- Uses **virtual → physical address translation**
- Loads **only required pages**
- Handles **page faults**