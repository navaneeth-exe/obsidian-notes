## **Definition**

I/O Mapped I/O is a device interaction technique in which **input/output devices are assigned a separate address space** different from the main memory.  
The CPU communicates with these devices using **special I/O instructions**.

---

## **Key Idea**

👉 Memory and I/O are treated **separately**  
👉 Devices are accessed using **dedicated instructions**, not normal memory instructions

---

## **How It Works**

1. Each I/O device is given a **unique port address**.
2. CPU uses **special instructions** like:
    - **IN** → to read data from device
    - **OUT** → to send data to device
3. Data transfer happens through **CPU registers** (usually accumulator).
4. Control signals specify whether it's an I/O operation.

---

## **Example**

- Keyboard → Input device
- Printer → Output device

CPU executes:

- `IN` → to read from keyboard
- `OUT` → to send data to printer

---

## **Features**

- Separate **I/O address space**
- Uses **special instructions (IN/OUT)**
- Limited number of I/O ports
- Does **not use normal load/store instructions**

---

## **Advantages**

✔ No interference with memory address space  
✔ Simpler hardware design  
✔ Clear distinction between memory and I/O operations

---

## **Disadvantages**

❌ Requires special instructions (less flexible)  
❌ Limited number of I/O addresses  
❌ Slightly slower compared to memory-mapped I/O

---

## **Diagram (write if needed in exam)**

```
        CPU  
         |  
   ----------------  
   |              |  
Memory        I/O Devices  
(Address)     (Port Address)
```