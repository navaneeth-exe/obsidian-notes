### Definition

### Refer this too : https://chatgpt.com/share/69f83738-1a70-8323-9e30-bdca63d94b58
The **Fetch–Decode–Execute cycle** is the basic operation performed by the CPU to execute every instruction stored in memory.

---

## 1️⃣ Fetch Phase

- The address of the next instruction is stored in the **Program Counter (PC)**.
- Instruction is fetched from **main memory**.
- The fetched instruction is loaded into the **Instruction Register (IR)**.
- PC is incremented to point to the next instruction.

📌 **Key points to write:**

- PC → Memory → IR
- Instruction is fetched from memory

---

## 2️⃣ Decode Phase

- The **Control Unit (CU)** decodes the instruction in IR.
- Determines:
    - What operation to perform
    - Which operands are needed
- Generates control signals for execution.

📌 **Key points to write:**

- Instruction decoding
- Operand identification
- Control signal generation

---

## 3️⃣ Execute Phase

- The instruction is executed by the **ALU** or other units.
- Arithmetic or logical operation is performed.
- Result is stored in a register or memory.

📌 **Key points to write:**

- ALU performs operation
- Result stored or output produced

---

## (Optional) Store Phase (Mention if needed)

- The result is written back to:
    - Memory, or
    - Register, or
    - Output device


![[Pasted image 20260404151854.png]]