## **1. Timer**

### **Definition**

A **timer** is a hardware module in a microcontroller used to **count clock pulses** to measure time intervals or generate delays.

### **Working**

- Timer increments count based on **clock signal**
- When count reaches a limit → **overflow occurs**
- Can generate **interrupts**

### **Uses**

- Time delay generation
- Event counting
- Pulse generation

---

## **2. ADC (Analog-to-Digital Converter)**

### **Definition**

ADC converts **analog signals (continuous)** into **digital values (binary form)**.

### **Working**

- Takes analog input voltage
- Samples and quantizes it
- Produces equivalent **digital output**

### **Uses**

- Sensor interfacing
- Temperature, light measurement
- Data acquisition systems

---

## **3. DAC (Digital-to-Analog Converter)**

### **Definition**

DAC converts **digital data** into **analog signal (voltage/current)**.

### **Working**

- Receives binary input
- Produces proportional analog output

### **Uses**

- Audio output
- Motor control
- Signal generation

---

## **4. Watchdog Timer (WDT)**

### **Definition**

A watchdog timer is a **safety timer** used to **reset the system automatically** if the program fails or hangs.

### **Working**

- Runs continuously in background
- Must be **reset periodically by program**
- If not reset → system **restarts**

### **Uses**

- Prevent system crash
- Improves reliability
- Used in embedded and real-time systems

---

## **Key Points for Exam 💯**

- Timer → measures time
- ADC → analog → digital
- DAC → digital → analog
- Watchdog → system safety/reset