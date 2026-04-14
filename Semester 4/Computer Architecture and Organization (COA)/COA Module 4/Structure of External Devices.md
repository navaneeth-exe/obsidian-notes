## **Definition**

External devices are hardware components that allow a computer system to **communicate with the outside environment**, such as input, output, and communication devices.

---

## **Basic Structure**

An external device is **not directly connected to CPU**, instead it communicates through an **I/O module** due to speed mismatch.

👉 Overall connection:  
**CPU → I/O Module → External Device**

---

## **Components of External Device**

An external device mainly consists of **three parts**:
![[Pasted image 20260415013506.png]]
---

## **1. Control Logic**

### **Function**

- Controls the operation of the device
- Receives control signals from I/O module
- Coordinates data transfer

### **Key Point**

Acts as the **brain of the device**

---

## **2. Transducer**

### **Function**

- Converts **physical signals ↔ electrical signals**
- Used in both input and output devices

### **Example**

- Keyboard → key press → electrical signal
- Speaker → electrical signal → sound

---

## **3. Buffer**

### **Function**

- Temporarily stores data during transfer
- Matches speed difference between device and system

### **Key Point**

Prevents data loss during transfer

---

## **Signals Used in Communication**

External device communicates with I/O module using:

- **Data Signals** → transfer actual data
- **Control Signals** → commands (read/write)
- **Status Signals** → device state (ready/busy)

---

# **Working of External Device (Exam Answer)**

## **Working (Step-by-Step)**

1. **Request from CPU**
    - CPU sends a command to the **I/O module** through the system bus
    - Specifies operation (read/write)

---

2. **Control Signal to Device**
    - I/O module sends **control signal** to the external device
    - Indicates what action to perform

---

3. **Activation of Control Logic**
    - Control logic inside device receives the signal
    - It **controls and manages device operation**

---

4. **Signal Generation (Transducer)**
    - Transducer interacts with environment
    - Converts:
        - Physical signal → electrical signal (input)
        - Electrical signal → physical output

---

5. **Data Conversion & Buffering**
    - Control logic converts signal into **binary data**
    - Data stored temporarily in **buffer**

---

6. **Status Signal to I/O Module**
    - Device sends **status signal (READY/BUSY)**
    - Indicates whether data is available

---

7. **Data Transfer to I/O Module**
    - Buffered data is sent to I/O module
    - Through **data lines**

---

8. **Transfer to CPU**
    - I/O module transfers data to CPU
    - CPU reads data and continues execution


---

## **Example (Keyboard Input)**

- Key pressed → signal generated
- Transducer converts to electrical signal
- Control logic processes → converts to binary
- Stored in buffer
- Sent to CPU via I/O module


# **Working of External Device (Exam Answer – Short & Complete)**

## **Working**

1. CPU sends request to **I/O module** via system bus
2. I/O module sends **control signal** to external device
3. **Control logic** activates device and manages operation
4. **Transducer** converts physical signal ↔ electrical signal
5. Signal converted to **binary data**
6. Data stored temporarily in **buffer**
7. Device sends **status signal (ready/busy)** to I/O module
8. Data transferred to **I/O module → CPU**