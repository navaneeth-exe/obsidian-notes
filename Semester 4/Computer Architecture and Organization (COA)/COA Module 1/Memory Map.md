## 🔥 Definition

👉 A **memory map** is the layout of how the total memory of a computer system is organized and allocated to different components like RAM, ROM, stack, heap, OS, and I/O devices.

---

## 🧠 Key Idea

👉 It shows:

- Where programs are loaded
- Where data is stored
- Where OS and devices are located
- How memory is managed

---

# 🧱 Structure of Memory Map

A typical memory map divides memory into the following regions:

---

## 1️⃣ ROM (Boot Area)

- Stores **bootloader and firmware**
- Execution starts from here when power ON
- Non-volatile

---

## 2️⃣ RAM (Main Memory)

- Stores currently executing programs
- Volatile memory
- Directly accessed by CPU

---

### 🔹 Inside RAM:

### 📌 Stack

- Stores:
    - Function calls
    - Local variables
    - Return addresses
- Works in **LIFO**
- Fast but limited size

---

### 📌 Heap

- Used for **dynamic memory allocation**
- Flexible but slower than stack

---

### 📌 Data Segment

- Stores:
    - Global variables
    - Static variables

---

## 3️⃣ Text Segment

- Stores **machine instructions (program code)**
- Read-only in most cases

---

## 4️⃣ OS Area

- Reserved for **operating system kernel**
- Manages system resources
- Protected from user programs

---

## 5️⃣ Memory-Mapped I/O (MMIO)

- Part of memory used for **I/O devices**
- Devices are accessed using normal memory instructions

---

# 🧾 Diagram (VERY IMPORTANT FOR FULL MARKS)

```
High Address  
-------------------------  
|   OS + I/O (MMIO)     |  
-------------------------  
|        Stack          |  
-------------------------  
|        Heap           |  
-------------------------  
|     Data Segment      |  
-------------------------  
|     Text Segment      |  
-------------------------  
|         ROM           |  
-------------------------  
Low Address

```
---



## 🧱 Segments of Memory Map

### 1️⃣ Text Segment

- Stores program instructions (code)

---

### 2️⃣ Global Data Segment

- Stores global variables
- Accessible by all functions

---

### 3️⃣ Dynamic Data Segment

- Stores local and temporary variables
- Used for dynamic memory allocation

---

### 4️⃣ Operating System Segment

- Reserved for OS
- Handles system-level operations

---

### 5️⃣ Exception Handler Segment

- Stores error-handling routines
- Executes during exceptions (e.g., divide by zero)

---

# 🧾 Diagram (WRITE THIS = FULL MARKS)

```
High Address  
-------------------------  
|   Operating System     |  
-------------------------  
|   Dynamic Data        |  
-------------------------  
|   Global Data         |  
-------------------------  
|   Text Segment        |  
-------------------------  
| Exception Handlers    |  
-------------------------  
Low Address
```

---

# ⚡ Key Points to Add (for extra marks)

- Memory is divided into **logical regions**
- Helps in **efficient memory management**
- Ensures **protection and organization**
- Used by OS for allocation and control

