## **Definition**

**Programmed I/O** is an I/O technique in which the CPU controls the entire data transfer process by continuously checking the status of the I/O device until it is ready.

---

## **Working Mechanism**

1. The CPU issues an I/O command to the device controller.
2. The CPU repeatedly checks the **status register** of the device (**polling**).
3. If the device is not ready, the CPU keeps waiting (busy waiting).
4. Once the device is ready, the CPU performs data transfer.
5. The process repeats until all data is transferred.

---

## **Block Diagram**

_(Draw this in exam)_

```
CPU  <---->  Device Controller  <---->  I/O Device
```

---

## **Key OS Concepts Used**

- **Polling**
- **Busy Waiting**
- **Device Controller**
- **Status Register**

---

## **Features**

- CPU is actively involved in every step.
- No interrupts are used.
- CPU waits until I/O completes.

---

## **Advantages**

- Simple to implement
- No need for interrupt hardware
- Suitable for simple or low-speed devices

---

## **Disadvantages**

- Wastes CPU time (busy waiting)
- Poor CPU utilization
- Not suitable for multitasking systems

---

## **Conclusion**

Programmed I/O is inefficient because the CPU remains busy waiting for the I/O device, making it unsuitable for modern operating systems where efficient CPU utilization is required.