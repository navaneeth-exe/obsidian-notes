## ⚙️ Step 1: Assembler

👉 **Definition:**  
Assembler is a system program that converts **assembly language into object file containing machine code**

---

### 🔹 Process done by Assembler:

1. Reads source program line by line
2. Translates mnemonics → binary (opcode)
    - Example: ADD → binary code
3. Converts operands
    - Registers → binary codes
    - Constants → binary values
4. Generates **object file** containing:
    - Machine code
    - Data

---

### 📦 Output:

👉 **Object File (.obj / .o)**

- Not directly executable

---

## 🔗 Step 2: Linker

👉 **Definition:**  
Linker is a system program that converts **object file into executable file**

---

### 🔹 Process done by Linker:

1. Combines one or more object files
2. Assigns memory addresses to variables and functions
3. Resolves external references
4. Generates final **executable file**

---

### 📦 Output:

👉 **Executable File (.exe)**

- Can be run by CPU

---

## ⚡ Final Step:

After linking,  
👉 Program is **loaded into memory and executed by CPU**

---

# 🔥 Complete Flow (IMPORTANT)

```
Source Program (Assembly Code)  
        ↓  
Assembler  
        ↓  
Object File  
        ↓  
Linker  
        ↓  
Executable File  
        ↓  
Execution by CPU
```