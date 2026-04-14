### 👉 Example: `sw x5, 4(x9)`

(Store word: store data from register into memory)

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
    - `rs2 (x5)` → source register (data to store)
    - `imm (4)` → offset value
- Control unit generates required control signals.

---

## **3. Register Read**

- Register file reads:
    - **x9 → RD1** (base address)
    - **x5 → RD2** (data to be stored)

---

## **4. Immediate Generation**

- Immediate value is taken from instruction bits (31–25 and 11–7).
- It is **sign-extended to 32 bits** using the extender.

📌 (Shown in S-type format explanation)

---

## **5. Effective Address Calculation**

- ALU performs addition:
    - Input 1 → base address (from RD1)
    - Input 2 → extended immediate

👉 Effective Address = Base + Offset

---

## **6. Memory Access**

- ALU output is given to **Data Memory** as address.
- RD2 (data from x5) is given to **write data input** of memory.
- Since it is a store instruction:
    - **MemWrite = 1 → Write operation**

👉 Data is stored in memory at the computed address.

📌 (From datapath explanation page 6)

---

## **7. Write Back**

- ❌ No write back to register file
- Because data is stored in memory, not in a register

---

## **8. PC Update**

- PC is updated to next instruction:  
    👉 **PC = PC + 4**

📌 (Page 7 diagram)

---

# ✅ **Control Signals for `sw`**

|Control Signal|Value|
|---|---|
|ALUSrc|1|
|MemWrite|1|
|RegWrite|0|
|ResultSrc|X (don’t care)|
|ALUControl|ADD|

---

# 🧠 **Final Conclusion (Must Write)**

👉 The `sw` instruction reads base and source registers, computes the effective address using ALU, writes data from register into memory, and updates the PC.