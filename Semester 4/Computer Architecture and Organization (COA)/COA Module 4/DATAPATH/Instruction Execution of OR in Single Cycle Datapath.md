
Refer ms notes

### 👉 Example: `or x4, x5, x6`

(R-type: perform OR between x5 and x6, store in x4)

---

## **1. Instruction Fetch**

- The **Program Counter (PC)** holds the address of the instruction.
- PC sends this address to **Instruction Memory**.
- Instruction memory fetches the instruction and outputs it.

📌 (Matches datapath diagram page 3)

---

## **2. Instruction Decode**

- The instruction is decoded into fields:
    - `rs1 (x5)` → source register 1
    - `rs2 (x6)` → source register 2
    - `rd (x4)` → destination register
- Control unit generates required control signals.

---

## **3. Register Read**

- Register file reads:
    - **x5 → RD1**
    - **x6 → RD2**

📌 (From datapath explanation: both registers are read simultaneously)

---

## **4. Immediate Generation**

- ❌ Not required for R-type instruction.
- ALU uses only register values (no extender used).

---

## **5. ALU Operation**

- ALU performs OR operation:
    - Input 1 → RD1 (x5)
    - Input 2 → RD2 (x6)

👉 Result = x5 OR x6

📌 ALU Control signal decides operation  
📌 For OR → ALUControl = 011 (from PDF)

---

## **6. Memory Access**

- ❌ Not used
- No data memory read/write for R-type instruction

---

## **7. Write Back**

- ALU result is written back to destination register **x4**
- Controlled by **RegWrite = 1**

📌 (Result comes from ALU, not memory)

---

## **8. PC Update**

- PC is updated to next instruction:  
    👉 **PC = PC + 4**

---

# ✅ **Control Signals for `or`**

|Control Signal|Value|
|---|---|
|ALUSrc|0|
|MemWrite|0|
|RegWrite|1|
|ResultSrc|0|
|ALUControl|OR (011)|

---

# 🧠 **Final Conclusion (Must Write)**

👉 The `or` instruction reads two source registers, performs OR operation using ALU, writes the result into the destination register, and updates the PC.