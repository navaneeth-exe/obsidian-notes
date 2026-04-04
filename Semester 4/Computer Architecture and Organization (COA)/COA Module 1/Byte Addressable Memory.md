### Definition

**Byte addressable memory** is a memory organization in which **each individual byte has a unique memory address**.  
This means the **smallest unit that can be addressed is 1 byte (8 bits)**.

📌 **Key exam line:**

> In byte addressable memory, each address refers to a single byte.

---

## Explanation

- Memory is divided into **bytes (8 bits each)**.
- Every byte is assigned a **separate address**.
- If a word consists of multiple bytes, it occupies **consecutive memory addresses**.
- CPU accesses memory using **byte addresses**.

---

## Example (Very Important 🔥)

Assume:

- Word size = **32 bits (4 bytes)**
- Memory starts at address **1000**

|Address|Stored Data|
|---|---|
|1000|Byte 0|
|1001|Byte 1|
|1002|Byte 2|
|1003|Byte 3|

👉 One 32-bit word occupies **4 consecutive byte addresses**.

---

## How Data is Accessed

- To read a **byte** → CPU accesses one address.
- To read a **word** → CPU accesses multiple consecutive byte addresses.

---

## Advantages of Byte Addressable Memory

- Efficient handling of **characters and strings**.
- Flexible data access.
- Supports different data sizes (byte, half-word, word).