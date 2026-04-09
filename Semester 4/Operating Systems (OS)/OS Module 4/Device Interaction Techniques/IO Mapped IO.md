## **Definition**

**I/O Mapped I/O** is a technique where I/O devices are assigned a **separate address space** different from main memory, and special CPU instructions are used to perform I/O operations.

---

## **Working Mechanism**

1. Each I/O device is assigned a unique **I/O address**.
2. CPU uses **special instructions** (like `IN` and `OUT`) to communicate with devices.
3. The address is placed on the address bus.
4. The control unit identifies it as an **I/O operation** (not memory).
5. Data is transferred between CPU and the I/O device through registers.

---

## **Block Diagram**



```
CPU  <---->  I/O Ports  <---->  I/O Device
```

---

## **Key Characteristics**

- Separate address space for I/O and memory
- Uses special instructions (`IN`, `OUT`)
- Limited number of I/O addresses
- Clear distinction between memory and I/O

---

## **Advantages**

- No conflict between memory and I/O addresses
- Simplifies hardware design
- Faster identification of I/O operations

---

## **Disadvantages**

- Requires special instructions (less flexible)
- Limited address space for I/O devices
- Cannot use all memory instructions for I/O

---

## **Example**

- Reading from keyboard using `IN` instruction
- Writing to printer using `OUT` instruction

---

## **Conclusion**

I/O mapped I/O provides a clear separation between memory and I/O operations using dedicated instructions, but its limited flexibility and address space make it less efficient compared to memory-mapped I/O.