## **Definition**

Shift instructions in RISC-V are used to **move (shift) bits left or right** within a register.  
They are commonly used for:

- Fast multiplication/division
- Bit manipulation

---

## **Types of Shift Instructions**

### **1. Shift Left Logical (SLL)**

- Shifts bits to the **left**
- Vacated rightmost bits are filled with **0**

**Format:**  
`sll rd, rs1, rs2`

👉 Shifts by value in `rs2`

**Immediate version:**  
`slli rd, rs1, imm`

**Example:**

```
slli x1, x2, 2   # x1 = x2 << 2 (multiply by 4)
```

---

### **2. Shift Right Logical (SRL)**

- Shifts bits to the **right**
- Leftmost bits are filled with **0**

**Format:**  
`srl rd, rs1, rs2`

**Immediate version:**  
`srli rd, rs1, imm`

**Example:**

```
srli x1, x2, 1   # x1 = x2 >> 1 (divide by 2)
```

---

### **3. Shift Right Arithmetic (SRA)**

- Shifts bits to the **right**
- Preserves the **sign bit** (MSB)

**Format:**  
`sra rd, rs1, rs2`

**Immediate version:**  
`srai rd, rs1, imm`

**Example:**

```
srai x1, x2, 1   # maintains sign for negative numbers
```
---

## **Summary Table**

|Instruction|Description|
|---|---|
|sll / slli|Shift left logical|
|srl / srli|Shift right logical|
|sra / srai|Shift right arithmetic|

---

## **Example**

addi x1, x0, 8      # 1000  
slli x2, x1, 1      # 10000 → 16  
srli x3, x1, 1      # 0100 → 4

---

## **Key Points**

- Left shift = **multiplication by 2ⁿ**
- Right shift = **division by 2ⁿ**
- `SRA` keeps sign (important for negative numbers)
- Used in **bit manipulation and optimization**

---

## **Conclusion**

Shift instructions in RISC-V provide an efficient way to perform **fast arithmetic operations and bit-level manipulation**.