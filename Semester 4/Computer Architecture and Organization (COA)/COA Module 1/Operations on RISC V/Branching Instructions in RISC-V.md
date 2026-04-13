## **Definition**

Branching instructions are used to **change the flow of program execution based on a condition**.

👉 Instead of executing instructions sequentially, the program can **jump to another location**.

📌 As per your notes (page 12):  
“Branching allows a program to change its operation based on condition.”

---

## **Types of Branching Instructions**

### **1. Conditional Branching**

- Execution changes **only if a condition is true**

### **2. Unconditional Branching**

- Execution **always jumps** to another location (no condition)

---

## **Conditional Branch Instructions**

|Instruction|Meaning|Condition|
|---|---|---|
|beq|Branch if equal|rs1 = rs2|
|bne|Branch if not equal|rs1 ≠ rs2|
|blt|Branch if less than|rs1 < rs2|
|bge|Branch if greater or equal|rs1 ≥ rs2|
|bltu|Branch if less than (unsigned)|rs1 < rs2|
|bgeu|Branch if greater or equal (unsigned)|rs1 ≥ rs2|

📌 These match exactly what’s listed in your notes table (page 12)

---

## **Format**

branch_instruction rs1, rs2, label

👉 If condition is true → jump to **label**  
👉 Else → continue next instruction

---

## **Example**

```
addi s0, x0, 4  
addi s1, x0, 4  
  
beq s0, s1, target   # if equal, jump  
  
addi s2, x0, 10      # skipped if branch taken  
  
target:  
add s3, s0, s1
```

---

## **Unconditional Branching (Jump)**

- `jal` → Jump and link
- Used to **jump to another address without condition**

📌 From your notes (page 13):  
“Jump is an unconditional branch that transfers control without checking any condition.”

---

## **Key Points**

- Used for **decision making & loops**
- Works using **labels (target addresses)**
- Conditional → depends on comparison
- Unconditional → always jumps