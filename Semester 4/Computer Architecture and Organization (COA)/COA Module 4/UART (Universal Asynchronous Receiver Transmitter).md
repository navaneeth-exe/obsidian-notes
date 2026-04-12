## **Definition**

UART is a **hardware communication module** used for **serial data transmission and reception** between two devices **without using a common clock signal**.

---

## **Basic Concept**

- It is an **asynchronous communication protocol**
- No shared clock → both devices agree on a **baud rate**
- Data is transmitted **bit-by-bit**
- Uses only **two lines: TX and RX**

---

## **Basic Communication Setup**

```
Device 1 (Transmitter)       Device 2 (Receiver)  
-----------------------------------------------  
TX  -----------------------> RX  
RX  <----------------------- TX

```
👉 Important: **Cross connection (TX ↔ RX)**

---

## **Components / Terminology**

- **DTE (Data Terminal Equipment)** → Microcontroller / Computer
- **DCE (Data Communication Equipment)** → Modem / Peripheral device

---

## **UART Data Frame (VERY IMPORTANT 🔥)**

A single data packet is transmitted in the form of a **frame**:

```
Start Bit | Data Bits | Parity Bit (optional) | Stop Bit
```

---

## **Explanation of Frame Fields**

### **1. Start Bit**

- Indicates beginning of transmission
- Logic changes from **1 → 0**
- Alerts receiver

---

### **2. Data Bits**

- Actual data (usually **8 bits**)
- Sent **LSB first**

---

### **3. Parity Bit (Optional)**

- Used for **error detection**
- Types:
    - Even parity
    - Odd parity

---

### **4. Stop Bit**

- Indicates end of transmission
- Logic = **1**

---

# **Working of UART**

1. When no data is transmitted, the line remains at **logic HIGH (idle state)**.
2. Transmission starts with a **start bit (0)**, indicating beginning of data.
3. The transmitter sends **data bits one by one** (usually 8 bits, LSB first) at a fixed **baud rate**.
4. An optional **parity bit** is added for error detection.
5. A **stop bit (1)** is sent to indicate end of transmission.
6. The receiver detects the start bit and **samples each bit at correct time intervals** to reconstruct the data


---

## **Features**

- **Asynchronous communication**
- No need for clock signal
- Simple implementation
- Supports **full duplex**

---

## **Advantages**

- Requires only **2 wires (TX, RX)**
- Easy to implement
- Low hardware complexity

---

## **Disadvantages**

- **Slower than SPI**
- Error detection is limited (parity only)
- Not suitable for high-speed applications

---

## **Applications**

- Serial communication between computers
- Microcontroller communication
- GPS, Bluetooth modules