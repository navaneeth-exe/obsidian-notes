## **Definition**

Addressing modes are the methods used by the CPU to **identify the location of operands** required for an instruction.

---

## **Types of Addressing Modes**

---

## **1. Register Addressing Mode**

### **Explanation**

Operands are stored in **CPU registers**, and the instruction directly uses those registers.

### **Example**

```
ADD R1, R2, R3
```

👉 R1 = R2 + R3

### **Points**

- Very fast (no memory access)
- Used in most arithmetic operations

---

## **2. Immediate Addressing Mode**

### **Explanation**

Operand value is **given directly inside the instruction**.

### **Example**

```
ADDI R1, R2, 5
```

👉 R1 = R2 + 5

### **Points**

- No need to fetch from memory
- Faster execution

---

## **3. Base (Register Indirect) Addressing Mode**

### **Explanation**

Operand is stored in **memory**, and its address is calculated using a base register and offset.

### **Formula**

Effective Address = Base Register + Offset

### **Example**

```
LW R1, 4(R2)
```

👉 R1 = Memory[R2 + 4]

### **Points**

- Used in load/store instructions
- Flexible for accessing arrays and data

---

## **4. PC Relative Addressing Mode**

### **Explanation**

Address of operand is calculated using **Program Counter (PC)** and an offset.

### **Formula**

```
Target Address = PC + Offset
```

### **Example**

```
BEQ R1, R2, LABEL
```

👉 If condition true → jump to new address

### **Points**

- Used in branching
- Helps in loops and decision making

---

## **Key Points (Write this 💯)**

- Defines how CPU accesses operands
- Improves flexibility of instructions
- Common types:
    - Register
    - Immediate
    - Base
    - PC-relative