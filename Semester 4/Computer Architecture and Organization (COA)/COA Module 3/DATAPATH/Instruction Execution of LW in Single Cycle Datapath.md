### 👉 Example: `lw x5, 4(x9)`

---

## **1. Instruction Fetch**

- The **Program Counter (PC)** holds the address of the instruction.
- PC sends this address to **Instruction Memory**.
- Instruction memory fetches the instruction and outputs it.

📌 (Matches datapath diagram page 3)

---

## **2. Instruction Decode**

- The instruction is decoded into fields:
    - `rs1 (x9)` → base register
    - `rd (x5)` → destination register
    - `imm (4)` → offset value
- Control unit generates required control signals.

---

## **3. Register Read**

- Register file reads the content of **x9** using `rs1`.
- Output is available at **RD1**.

---

## **4. Immediate Generation**

- The 12-bit immediate value is extracted from instruction bits.
- It is **sign-extended to 32 bits** using the extender.

📌 (Shown in page 5 diagram)

---

## **5. Effective Address Calculation**

- ALU performs addition:
    - Input 1 → base address (from RD1)
    - Input 2 → extended immediate

👉 Effective Address = Base + Offset

---

## **6. Memory Access**

- ALU output is given to **Data Memory** as address.
- Since it is a load instruction:
    - **MemWrite = 0 → Read operation**
- Data at that address is fetched.

---

## **7. Write Back**

- Data from memory is written into destination register **x5**.
- Controlled by **RegWrite = 1**.

📌 (Page 6 explanation)

---

## **8. PC Update**

- PC is updated to next instruction:
    - **PC = PC + 4**

📌 (Page 7 diagram)

---

# ✅ **Control Signals for `lw`**

|Control Signal|Value|
|---|---|
|ALUSrc|1|
|MemWrite|0|
|RegWrite|1|
|ResultSrc|1|
|ALUControl|ADD|

---

# 🧠 **Final Conclusion (Must Write)**

👉 The `lw` instruction reads the base register, adds the offset using ALU to form the effective address, fetches data from memory, writes it into the destination register, and updates the PC.