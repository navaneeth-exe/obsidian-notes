## **Definition**

**Interrupt-Driven I/O** is an I/O technique in which the CPU initiates an I/O operation and continues execution. The I/O device interrupts the CPU when it is ready for data transfer.

---

## **Working Mechanism**

1. The CPU issues an I/O command to the device controller.
2. The CPU continues executing other processes.
3. When the I/O device is ready, it sends an **interrupt request (IRQ)**.
4. The CPU completes the current instruction.
5. The CPU saves the current process state (**context saving**).
6. Control is transferred to the **Interrupt Service Routine (ISR)**.
7. The ISR performs data transfer between device and memory/CPU.
8. After completion, the CPU restores the previous context.
9. Execution of the interrupted process resumes.

---

## **Block Diagram**

```
        Interrupt Signal  
              ↑  
CPU  <---->  Device Controller  <---->  I/O Device
```

---

## **Key OS Concepts Used**

- **Interrupt Request (IRQ)**
- **Interrupt Service Routine (ISR)**
- **Context Switching**
- **Device Controller**

---

## **Advantages**

- Efficient CPU utilization (no busy waiting)
- Supports multitasking
- Better performance than Programmed I/O

---

## **Disadvantages**

- Overhead due to context switching
- Complex to implement
- Handling multiple interrupts can be difficult