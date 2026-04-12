## **Definition**

A single cycle datapath is a processor design in which **each instruction is executed completely in one clock cycle**.

---

## **Basic Concept**

- All stages of instruction execution happen in **one cycle**:
    - Instruction Fetch
    - Decode
    - Execute
    - Memory Access
    - Write Back

---

## **Main Components of Datapath**

1. **Program Counter (PC)**
    - Holds address of next instruction
2. **Instruction Memory**
    - Stores instructions
3. **Register File**
    - Stores operands and results
4. **ALU (Arithmetic Logic Unit)**
    - Performs operations
5. **Data Memory**
    - Used for load/store instructions
6. **Multiplexers (MUX)**
    - Select appropriate inputs
7. **Control Unit**
    - Generates control signals

---

## **Working**

1. PC sends address → instruction is fetched
2. Instruction is decoded
3. Operands are read from registers
4. ALU performs required operation
5. Data memory accessed (if needed)
6. Result is written back to register
7. PC updated to next instruction