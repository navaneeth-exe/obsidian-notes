### **Definition**

**Serial communication** is a method of data transmission in which data is sent **one bit at a time** over a single communication channel or wire.

---
### **Definition**

**Serial communication** is a method of data transmission in which data is sent **one bit at a time** over a single communication channel or wire.

---

### **Basic Concept**

- Data bits are transmitted **sequentially**.
- Requires **fewer wires** compared to parallel communication.
- Suitable for **long-distance communication**.

---

### **Block Diagram (How to draw in exam)**

Draw this simple flow:

Sender → Serializer → Transmission Medium → Deserializer → Receiver

- **Serializer**: Converts parallel data to serial
- **Deserializer**: Converts serial data back to parallel
### **Basic Concept**

- Data bits are transmitted **sequentially**.
- Requires **fewer wires** compared to parallel communication.
- Suitable for **long-distance communication**.

---

### **Block Diagram (How to draw in exam)**

Draw this simple flow:

```
Sender → Serializer → Transmission Medium → Deserializer → Receiver
```

- **Serializer**: Converts parallel data to serial
- **Deserializer**: Converts serial data back to parallel

---

### **Types of Serial Communication**

#### **1. Asynchronous Serial Communication**

- No common clock signal.
- Data sent with **start and stop bits**.
- Example: RS-232

**Frame format:**

Start bit | Data bits | Parity bit (optional) | Stop bit

**Features:**

- Simple and low cost
- Slower compared to synchronous

---

#### **2. Synchronous Serial Communication**

- Uses a **common clock signal**.
- Data sent in **continuous stream**.
- No start/stop bits.

**Features:**

- Faster than asynchronous
- More efficient transmission

**Examples:** SPI, I2C

---

### **Advantages**

- Requires **less hardware (fewer wires)**
- **Reliable for long distances**
- Less interference/noise

---

### **Disadvantages**

- **Slower** than parallel communication
- Needs **conversion circuits** (serializer/deserializer)

---

### **Applications**

- Computer communication (USB, UART)
- Networking systems
- Microcontroller communication