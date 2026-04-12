## **Definition**

GPIO refers to **programmable pins of a microcontroller** used to **read digital inputs or send digital outputs** to external devices.

---

## **Basic Concept**

- Each GPIO pin can act as:
    - **Input pin** → receives signal
    - **Output pin** → sends signal
- Used for communication with external devices like **LED, switch, sensors**

---

## **GPIO Modes**

### **1. Input Mode**

- Used to **read signals from external devices**
- Voltage is interpreted as digital value:

|Voltage|Logic|
|---|---|
|~0V|0|
|~3.3V / 5V|1|

👉 Example:

- Switch pressed → Logic 1
- Switch open → Logic 0

---

### **2. Output Mode**

- Used to **send signals to external devices**
- Microcontroller sets:
    - Logic 1 → High voltage
    - Logic 0 → Low (ground)

👉 Example:

- Logic 1 → LED ON
- Logic 0 → LED OFF
- 
---

## **GPIO Registers (Important 🔥)**

GPIO is controlled using **memory-mapped registers**:

1. **Input Enable (input_en)** → Configure pin as input
2. **Input Value (input_val)** → read data 
3. **Output Enable (output_en)** → set pin as output
4. **Output Value (output_val)** → send data

---

# **Operation of GPIO (Exam Answer)**

## **1. Input Operation (Reading from GPIO)**

### **Steps**

1. **Configure GPIO pin as input**
    - Done by setting corresponding bit in **input enable register**
2. **Read the input value**
    - GPIO hardware continuously monitors voltage at the pin
    - Stores corresponding value in **input value register**
3. **Check the required bit**
    - Processor reads the specific bit
    - If bit = 1 → input HIGH
    - If bit = 0 → input LOW

### **Example**

- A **switch is connected to GPIO pin**
- If switch is **closed** → voltage HIGH → bit = **1**
- If switch is **open** → voltage LOW → bit = **0**
- A **pull-down resistor** ensures proper LOW when open

---

## **2. Output Operation (Writing to GPIO)**

### **Steps**

1. **Configure GPIO pin as output**
    - Done using **output enable register**
2. **Write output value**
    - Data is written into **output value register**
3. **Apply signal to device**
    - Bit = 1 → High voltage → device ON
    - Bit = 0 → Low voltage → device OFF

### **Example**

- An **LED is connected to GPIO pin**
- Bit = **1** → current flows → **LED ON**
- Bit = **0** → no current → **LED OFF**