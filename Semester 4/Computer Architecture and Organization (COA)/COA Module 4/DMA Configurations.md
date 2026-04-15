DMA configuration defines how the **DMA controller, CPU, memory, and I/O devices are interconnected**.

---

![[WhatsApp Image 2026-04-15 at 10.37.56 AM.jpeg]]
## 🔹 1. Single Bus Configuration

A single system bus connects CPU, memory, I/O devices, and DMA controller.

### ✔️ Working:

- DMA requests control of the bus
- CPU grants access and temporarily stops
- DMA transfers data directly between I/O and memory

### ✔️ Advantages:

- Simple and low-cost design

### ✔️ Disadvantages:

- Bus contention between CPU and DMA
- CPU remains idle during transfer
- Lower performance

---

## 🔹 2. Separate I/O Bus Configuration

Uses two buses:

- System bus (CPU ↔ Memory)
- I/O bus (DMA ↔ I/O devices)

DMA controller connects both buses

### ✔️ Working:

- DMA transfers data via I/O bus
- CPU can continue execution with minimal interruption

### ✔️ Advantages:

- Reduced bus contention
- Better performance than single bus

### ✔️ Disadvantages:

- More complex
- Higher cost

---

## 🔹 3. Integrated DMA and I/O Configuration

- DMA controller is directly connected to one or more I/O modules
- Data transfer between DMA and I/O **does not use the system bus**

### ✔️ Working:

- DMA communicates directly with I/O devices
- System bus is used **only when transferring data to/from memory**

### ✔️ Advantages:

- Reduced system bus usage
- Improved performance compared to single bus
- Efficient data transfer

### ✔️ Disadvantages:

- Complex design
- Higher cost