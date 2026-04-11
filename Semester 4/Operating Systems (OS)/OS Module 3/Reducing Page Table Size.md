## **Introduction (Why needed)**

In paging, each process maintains a **page table** to map virtual pages to physical frames.

- Large virtual address spaces → **huge number of pages**
- Hence → **very large page tables**

👉 This leads to:

- High memory overhead
- Inefficient memory usage

💡 OS goal: **store only what is needed (sparse usage)**

---

## **Techniques to Reduce Page Table Size**

---

# **1. Increasing Page Size**

## **Concept**

- Increase page size → fewer pages → fewer entries in page table

## **Effect**

- Page table size **reduces significantly**

## **Problem**

- Causes **internal fragmentation**  
    👉 Unused space inside a page is wasted

---

# **2. Hybrid Approach (Segmentation + Paging)**

## **Concept**

- Divide process into **logical segments** (code, heap, stack)
- Each segment has its **own page table**

## **Working**

- Logical address = **< segment, page, offset >**

1. Segment table → gives base of that segment’s page table
2. Page table → maps page to frame
3. Frame + offset → physical address

## **Key Insight**

👉 Only active segments need page tables  
👉 Reduces unnecessary memory usage

---

# **3. Multilevel Page Table (MOST IMPORTANT)**

## **Concept**

- Instead of one large linear page table  
    👉 Split it into **multiple smaller tables**

💡 Only allocate page tables **when needed**

---

## **Structure & Address Format**

![[Pasted image 20260412020705.png|379]]


👉 Virtual Address is divided into:

- **Page Directory Index (PDI)**
- **Page Table Index (PTI)**
- **Offset**

## **Address Format**

👉 Virtual Address split into:

```
VA = [ Page Directory Index | Page Table Index | Offset ]
```

- PDI → selects page directory
- PTI → selects page table
- Offset → location inside page

---

## **Working (Step-by-Step)**

1. CPU generates virtual address
2. Use **PDI** → access page directory
3. Get base address of page table
4. Use **PTI** → find frame number
5. Combine with offset → physical address

---

## **Key Idea (VERY IMPORTANT)**

👉 Page tables are **allocated on demand**  
👉 Unused address space → **no memory wasted**

---

## **Advantages**

- Supports **sparse address spaces**
- Saves memory
- Efficient for large programs

---

## **Disadvantages**

- More complex
- On TLB miss → **multiple memory accesses**