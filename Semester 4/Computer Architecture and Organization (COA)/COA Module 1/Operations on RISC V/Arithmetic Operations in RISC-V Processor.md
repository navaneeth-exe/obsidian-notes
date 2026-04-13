## **Definition**

Arithmetic operations in RISC-V are used to perform mathematical calculations such as **addition, subtraction, multiplication, and division** on data stored in registers.

RISC-V follows a **load–store architecture**, so all arithmetic operations are performed **only on registers**.

---

## **Types of Arithmetic Instructions**

### **1. Register–Register Operations (R-type)**

- Operate on two registers and store result in a register.

**Format:**  
`add rd, rs1, rs2`

**Examples:**

- `add x1, x2, x3` → x1 = x2 + x3
- `sub x4, x5, x6` → x4 = x5 − x6
- `mul x7, x8, x9` → x7 = x8 × x9
- `div x10, x11, x12` → x10 = x11 ÷ x12

---

### **2. Register–Immediate Operations (I-type)**

- One operand is a constant (immediate value).

**Format:**  
`addi rd, rs1, imm`

**Examples:**

- `addi x1, x2, 10` → x1 = x2 + 10
- `subi` ❌ (not available directly in RISC-V)  
    👉 Use: `addi x1, x2, -5`

---

## **Common Arithmetic Instructions**

|Instruction|Operation|
|---|---|
|add|Addition|
|sub|Subtraction|
|addi|Add immediate|
|mul|Multiplication|
|div|Division|
|rem|Remainder|

---

## **Example**

addi x1, x0, 5     # x1 = 5  
addi x2, x0, 10    # x2 = 10  
add  x3, x1, x2    # x3 = 15  
sub  x4, x2, x1    # x4 = 5

---

## **Key Points**

- Operations are performed **only on registers**
- Uses **simple instruction formats (R-type & I-type)**
- Immediate values are supported
- No direct memory arithmetic

---

## **Conclusion**

Arithmetic operations in RISC-V are **simple, efficient, and register-based**, which improves performance and makes the architecture easy to implement.