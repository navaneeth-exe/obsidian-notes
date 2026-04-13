## **Definition**

Logical instructions in RISC-V are used to perform **bitwise operations** on data stored in registers.  
These operations work **bit-by-bit** on binary values.

---

## **Types of Logical Instructions**

### **1. Register–Register (R-type)**

- Operate on two registers

**Examples:**

- `and rd, rs1, rs2` → Bitwise AND
- `or rd, rs1, rs2` → Bitwise OR
- `xor rd, rs1, rs2` → Bitwise XOR

---

### **2. Register–Immediate (I-type)**

- One operand is an immediate value

**Examples:**

- `andi rd, rs1, imm`
- `ori rd, rs1, imm`
- `xori rd, rs1, imm`

---

## **Common Logical Operations**

|Instruction|Operation|
|---|---|
|and|1 if both bits are 1|
|or|1 if at least one bit is 1|
|xor|1 if bits are different|
|andi|AND with immediate|
|ori|OR with immediate|
|xori|XOR with immediate|

---

## **Shift Logical Instructions**

- `sll rd, rs1, rs2` → Shift left logical
- `srl rd, rs1, rs2` → Shift right logical

👉 Immediate versions:

- `slli rd, rs1, imm`
- `srli rd, rs1, imm`

---

## **Example**

```
addi x1, x0, 5      # 0101  
addi x2, x0, 3      # 0011  
  
and x3, x1, x2      # 0001 → 1  
or  x4, x1, x2      # 0111 → 7  
xor x5, x1, x2      # 0110 → 6
```

---

## **Key Points**

- Operate on **individual bits**
- Work only on **registers**
- Used in **masking, flags, and condition checking**
- Include **shift operations** for bit manipulation