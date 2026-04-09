## **Definition**

Memory-Mapped I/O is a technique in which **I/O devices are assigned addresses within the same address space as the main memory**.  
The CPU communicates with devices using **normal memory instructions**.

---

## **Key Idea**

👉 Memory and I/O share the **same address space**  
👉 No special instructions needed — just **LOAD / STORE**

---

## **How It Works**

1. Each I/O device is assigned a **memory address**.
2. CPU uses normal instructions like:
    - **LOAD** → read data from device
    - **STORE** → write data to device
3. Device registers (data, status, control) are mapped into memory.
4. CPU treats devices like **memory locations**.

---

## **Example**

- Suppose printer is mapped at address `2000`
- CPU writes:
    
    STORE R1, 2000
    

👉 This sends data to the printer like writing to memory

---

## **Features**

- Common **address space** for memory and I/O
- Uses **normal instructions (LOAD/STORE)**
- Large number of addressable devices
- No need for special I/O instructions

---

## **Advantages**

✔ Faster data transfer 🚀  
✔ No need for special instructions  
✔ More flexible programming  
✔ Large address space for devices

---

## **Disadvantages**

❌ Reduces available memory space  
❌ More complex hardware  
❌ Needs careful address management

---

## **Diagram (write in exam if needed)**

```
        CPU  
         |  
   ----------------  
   |              |  
Memory + I/O (Shared Address Space)
```