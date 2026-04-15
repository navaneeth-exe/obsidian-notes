## **Definition**

**Direct Memory Access (DMA)** is an I/O technique in which data is transferred directly between the I/O device and main memory without continuous involvement of the CPU.

---
![[Pasted image 20260416014149.png|462]]
## **Working Mechanism**

1. The CPU initializes the DMA controller by providing:
    - Starting memory address
    - Number of bytes to transfer
    - Direction of transfer (read/write)
2. The CPU starts the DMA operation and continues executing other processes.
3. The DMA controller takes control of the system bus.
4. Data is transferred directly between the I/O device and main memory.
5. After completion, the DMA controller sends an **interrupt** to the CPU.
6. The CPU executes the **Interrupt Service Routine (ISR)** to acknowledge completion.

---

## **Block Diagram**

```
          System Bus  
   -------------------------  
   |        |             |  
 CPU     Memory     DMA Controller  
                        |  
                    I/O Device
```

---

## **Key OS Concepts Used**

- **DMA Controller**
- **Interrupt**
- **Bus Arbitration**
- **Direct Memory Transfer**

---

## **Features**

- CPU is not involved during data transfer
- High-speed data transfer
- Uses interrupt only after completion
- Reduces CPU overhead

---

## **Advantages**

- Efficient CPU utilization
- Faster data transfer
- Suitable for large data transfer (e.g., disk operations)

---

## **Disadvantages**

- Hardware complexity (DMA controller required)
- Bus contention may occur
- Cost is higher

---

## **Modes of DMA (Optional – write if you have time 💯)**

- **Burst Mode** – transfers entire block at once
- **Cycle Stealing Mode** – transfers one byte at a time
- **Transparent Mode** – transfers only when CPU is idle

---

## **Conclusion**

DMA improves system performance by allowing direct data transfer between memory and I/O devices with minimal CPU intervention, making it ideal for high-speed operations.