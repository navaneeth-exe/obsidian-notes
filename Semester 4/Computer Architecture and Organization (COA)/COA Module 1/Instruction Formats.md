

# Refer other pdf and notes in that folder

## **Definition**

Instruction format defines how an instruction is **represented in binary** and how its bits are divided into different fields such as **opcode, registers, and immediate values**.

---

## **Basic Concept**

- In RISC architecture, each instruction is typically **fixed length (32 bits)**
- These 32 bits are divided into fields:
    - **Opcode** → operation
    - **Register fields** → operands
    - **Immediate field** → constant value

---

## **Types of Instruction Formats**

---

## **1. R-Type (Register Format)**

### **Purpose**

Used for operations involving **only registers**

### **Format**

```
| funct7 | rs2 | rs1 | funct3 | rd | opcode |
```

### **Example**

`add rd, rs1, rs2`

👉 rd = rs1 + rs2

---

### **Key Points**

- Uses **3 registers**
- No immediate value
- Used for arithmetic operations

---

## **2. I-Type (Immediate Format)**

### **Purpose**

Used when instruction contains an **immediate value**

### **Format**

```
| imm | rs1 | funct3 | rd | opcode |
```

### **Example**

```
addi rd, rs1, 5
```

👉 rd = rs1 + immediate

---

### **Key Points**

- Includes **constant value (immediate)**
- Used in arithmetic and load instructions

---

## **3. S-Type (Store Format)**

### **Purpose**

Used for **store instructions**

### **Format**

```
| imm | rs2 | rs1 | funct3 | imm | opcode |
```
### **Example**

```
sw rs2, offset(rs1)
```

---

### **Key Points**

- Stores data from register to memory
- Uses base + offset addressing

---

## **4. B-Type (Branch Format)**

### **Purpose**

Used for **branching instructions**

### **Format**

```
| imm | rs2 | rs1 | funct3 | imm | opcode |
```

### **Example**

```
beq rs1, rs2, label
```

---

### **Key Points**

- Used for **conditional branching**
- Uses PC-relative addressing

---

## **5. J-Type (Jump Format)**

### **Purpose**

Used for **jump instructions**

### **Format**

```
| imm | rd | opcode |
```

### **Example**

```
jal rd, target
```

---

### **Key Points**

- Used for function calls
- Stores return address

---

## **Key Points (Write this 💯)**

- Instruction format divides **32-bit instruction into fields**
- Types:
    - R-type
    - I-type
    - S-type
    - B-type
    - J-type
- Helps CPU **decode and execute instructions**