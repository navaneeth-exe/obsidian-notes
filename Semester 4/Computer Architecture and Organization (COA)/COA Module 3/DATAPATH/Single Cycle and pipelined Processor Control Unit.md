## **1. Definition**

👉 The **control unit** in a single cycle processor is a combinational logic circuit that generates control signals required to execute an instruction in one clock cycle.

or

👉 In a single cycle processor, the **control unit** is a combinational circuit that generates control signals based on the instruction being executed.

- It examines specific fields of the instruction and produces signals to control datapath operations.

## **2. Function of Control Unit**

- It **decodes the instruction opcode**.
- Generates appropriate **control signals**.
- Controls the operation of:
    - ALU
    - Register File
    - Data Memory
    - Multiplexers

📌 From your PDF:  
“Control unit generates appropriate control signals using combinational logic”

---
## **2. Inputs to Control Unit**

The control unit takes the following instruction fields as input:

- **Opcode (op field)**
- **funct3 field**
- **funct7 field**

👉 These fields help identify the type of instruction and required operation.

📌 (Clearly shown in page 1 diagram)

---

## **3. Output – Control Signals**

The control unit generates several control signals to control datapath components:

### 🔥 Important Control Signals:

|Signal|Function|
|---|---|
|RegWrite|Enables writing into register file|
|ALUSrc|Selects ALU input (register / immediate)|
|ALUControl|Specifies ALU operation|
|MemWrite|Enables writing into data memory|
|ResultSrc|Selects ALU result or memory output|
|PCSrc|Determines next PC value|

📌 (Listed clearly in page 2)

---

## **4. Structure of Control Unit**

👉 The control unit is divided into **two parts**:

---

### 🔹 **1. Main Decoder**

- Takes **opcode** as input
- Determines **instruction type (R, I, S, etc.)**
- Generates main control signals:
    - RegWrite
    - ALUSrc
    - MemWrite
    - ResultSrc
    - ImmSrc
- Also generates internal signals:
    - **ALUOp**
    - **Branch**

📌 (Page 3 explanation)

---

### 🔹 **2. ALU Decoder**

- Generates **exact ALU operation**
- Inputs:
    - ALUOp (from main decoder)
    - funct3
    - funct7
    - opcode
- Output:
    - **ALUControl signal**

📌 (Page 4 diagram)

---

## **5. Working of Control Unit**

### ⚡ Step-by-step:

1. Instruction is fetched from instruction memory.
2. Opcode is sent to main decoder.
3. Main decoder generates high-level control signals.
4. ALUOp is sent to ALU decoder.
5. ALU decoder uses funct fields to determine exact operation.
6. Final control signals control datapath components (ALU, memory, registers).