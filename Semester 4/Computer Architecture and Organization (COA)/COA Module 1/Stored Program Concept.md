## **Definition**

The stored program concept means that **both instructions (program) and data are stored in the same memory**, and the CPU fetches them one by one for execution.

---

## **Basic Idea**

- Program is stored in **main memory**
- CPU executes instructions **sequentially**
- Instructions are treated just like **data in memory**

# then explain fetch decode ex cycle

---

## **Working (Step-by-Step)**

1. Program is loaded into memory
2. **Program Counter (PC)** holds address of next instruction
3. Instruction is fetched from memory
4. Instruction is decoded
5. Operation is executed
6. PC moves to next instruction

👉 This cycle repeats (Fetch–Decode–Execute cycle)

---

## **Example**

If a program contains:

```
LOAD R1, A  
ADD R1, B  
STORE R1, C

```
👉 All these instructions are stored in memory and executed one after another.

---

## **Key Features**

- Same memory for **data and instructions**
- Sequential execution
- Uses **Program Counter (PC)**
- Based on **Von Neumann architecture**

---

## **Advantages**

- Simple and flexible design
- Easy to modify programs
- Efficient use of memory

---

## **Key Points (Write this 💯)**

- Instructions stored in memory like data
- CPU fetches instructions using PC
- Execution follows **fetch-decode-execute cycle**