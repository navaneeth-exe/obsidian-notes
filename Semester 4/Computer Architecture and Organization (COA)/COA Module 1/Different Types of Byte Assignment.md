### What is Byte Assignment?

**Byte assignment** refers to the **order in which bytes of a multi-byte data (word)** are stored in **byte addressable memory**.

When a word occupies multiple bytes, the system must decide:  
👉 **Which byte goes to the lowest memory address?**

This leads to **two types of byte assignment**.

---

## 1️⃣ Big Endian Byte Assignment

### Definition

In **Big Endian**, the **Most Significant Byte (MSB)** of a word is stored in the **lowest memory address**, followed by the remaining bytes in decreasing significance.

📌 **Mnemonic:** _Big end first_

---

### Example (WRITE THIS IN EXAM 🔥)

Given:

- 32-bit number = `0x12345678`
- Starting memory address = `1000`

|Address|Content|
|---|---|
|1000|12 (MSB)|
|1001|34|
|1002|56|
|1003|78 (LSB)|

👉 Memory order matches **human reading order**.

---

### Characteristics of Big Endian

- MSB stored at lowest address
- Easier to understand and debug
- Network protocols follow Big Endian (network byte order)
- Address points to **most significant byte**

---

## 2️⃣ Little Endian Byte Assignment

### Definition

In **Little Endian**, the **Least Significant Byte (LSB)** of a word is stored in the **lowest memory address**, and the remaining bytes follow in increasing significance.

📌 **Mnemonic:** _Little end first_

---

### Example (VERY IMPORTANT 🔥)

Same data:

- 32-bit number = `0x12345678`
- Starting memory address = `1000`

|Address|Content|
|---|---|
|1000|78 (LSB)|
|1001|56|
|1002|34|
|1003|12 (MSB)|

👉 Address points to **least significant byte**.

---

### Characteristics of Little Endian

- LSB stored at lowest address
- Faster arithmetic operations
- Efficient for incrementing addresses
- Widely used in modern processors

---

## Byte Assignment & CPU Addressing (IMPORTANT CONCEPT)

- In **Big Endian**:
    - Address of word = address of MSB
- In **Little Endian**:
    - Address of word = address of LSB

This affects:

- Pointer arithmetic
- Data interpretation
- System interoperability