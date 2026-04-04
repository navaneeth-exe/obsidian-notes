### What is Byte Assignment?

**Byte assignment** refers to the **order in which bytes of a multi-byte data (word)** are stored in **byte addressable memory**.

When a word occupies multiple bytes, the system must decide:  
👉 **Which byte goes to the lowest memory address?**

This leads to **two types of byte assignment**.

---

## 1️⃣ Big Endian Byte Assignment

### Definition

In **Big Endian**, the **most significant byte (MSB)** is stored at the **lowest memory address**.

📌 _Simple rule:_

> **Big end first**

---

### Example

Assume:

- 32-bit data = `0x12345678`
- Starting address = `1000`

|Memory Address|Byte Stored|
|---|---|
|1000|12|
|1001|34|
|1002|56|
|1003|78|

👉 MSB (`12`) is stored first.

---

### Key Points

- Human-readable order
- Easier for debugging
- Used in some processors and network protocols

---

## 2️⃣ Little Endian Byte Assignment

### Definition

In **Little Endian**, the **least significant byte (LSB)** is stored at the **lowest memory address**.

📌 _Simple rule:_

> **Little end first**

---

### Example

Same data:

- 32-bit data = `0x12345678`
- Starting address = `1000`

|Memory Address|Byte Stored|
|---|---|
|1000|78|
|1001|56|
|1002|34|
|1003|12|

👉 LSB (`78`) is stored first.

---

### Key Points

- Faster arithmetic operations
- Widely used in modern processors
- Address points to least significant byte