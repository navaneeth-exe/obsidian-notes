## **Introduction**

When an interrupt occurs, the CPU must identify **which device generated the interrupt**. This is called **interrupt identification**, and several techniques are used.

---

## **1. Multiple Interrupt Lines**

### **Definition**

Each device is connected to the CPU using a **separate interrupt line**.

### **Working**

- Each device has its own interrupt request (IRQ) line.
- When a device interrupts, the CPU directly knows the source based on the line.

### **Advantages**

- Fast identification
- No ambiguity

### **Disadvantages**

- Requires more hardware lines
- Not scalable for many devices

---

## **2. Software Polling**

### **Definition**

The CPU checks each device one by one to find which device caused the interrupt.

### **Working**

1. An interrupt occurs.
2. CPU executes ISR.
3. ISR checks status registers of devices sequentially.
4. The device with a pending request is identified.

### **Advantages**

- Simple to implement
- No extra hardware required

### **Disadvantages**

- Time-consuming
- Inefficient for many devices

---

## **3. Daisy Chaining**

### **Definition**

Devices are connected in a **series (chain)**, and interrupt priority is determined by their position.

### **Working**

- Interrupt signal passes through devices one by one.
- The first device in the chain with a request captures the interrupt.
- Others pass the signal forward.

### **Advantages**

- Simple hardware design
- Built-in priority mechanism

### **Disadvantages**

- Fixed priority (not flexible)
- Failure of one device can affect others