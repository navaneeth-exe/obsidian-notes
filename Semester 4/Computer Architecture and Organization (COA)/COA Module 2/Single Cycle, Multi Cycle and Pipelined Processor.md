## **1. Single Cycle Processor**

### **Definition**

A single cycle processor executes **one complete instruction in a single clock cycle**.

### **Working**

- All stages (fetch, decode, execute, memory, write back) happen in **one cycle**

### **Advantages**

- Simple design
- Easy to implement

### **Disadvantages**

- Long clock cycle (slow)
- Inefficient for complex instructions

---

## **2. Multi Cycle Processor**

### **Definition**

A multi-cycle processor executes an instruction in **multiple clock cycles**, dividing execution into stages.

### **Working**

- Each stage (fetch, decode, execute, etc.) takes **one clock cycle**
- Same hardware reused in different cycles

### **Advantages**

- Shorter clock cycle
- More efficient than single cycle

### **Disadvantages**

- Control logic is more complex
- Takes multiple cycles per instruction

---

## **3. Pipelined Processor**

### **Definition**

A pipelined processor executes **multiple instructions simultaneously** by overlapping different stages.

### **Working**

- Instruction execution is divided into stages
- Each stage works in parallel on different instructions

### **Advantages**

- High performance
- Increased throughput

### **Disadvantages**

- Pipeline hazards (data, control, structural)
- Complex design

---

## **Key Points (Write this 💯)**

| Processor    | Execution                         |
| ------------ | --------------------------------- |
| Single Cycle | 1 instruction in 1 cycle          |
| Multi Cycle  | 1 instruction in multiple cycles  |
| Pipelined    | Multiple instructions in parallel |