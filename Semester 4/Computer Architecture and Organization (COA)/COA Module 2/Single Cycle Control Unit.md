## **Definition**

The single cycle control unit is a component that **generates control signals for executing an instruction in one clock cycle**.

---

## **Basic Concept**

- All instructions are executed in **one cycle**
- Control unit generates signals **based on instruction opcode**
- Works with **datapath components**

---

## **Working**

1. Instruction is fetched
2. Opcode is sent to control unit
3. Control unit decodes opcode
4. Generates required **control signals**
5. Signals control:
    - ALU operation
    - Register read/write
    - Memory access
    - Data path selection

---

## **Main Control Signals**

- **RegWrite** → Write data to register
- **MemRead** → Read from memory
- **MemWrite** → Write to memory
- **ALUOp** → Select ALU operation
- **ALUSrc** → Select ALU input
- **MemtoReg** → Select data source
- **PCSrc** → Update program counter

---

## **Key Points (Write this 💯)**

- Generates control signals in **single clock cycle**
- Based on **opcode decoding**
- Controls entire datapath
- Simple but requires **long clock cycle**

---

## **Important Line 😏**

Control signals are generated **once per instruction** since execution happens in a single cycle.