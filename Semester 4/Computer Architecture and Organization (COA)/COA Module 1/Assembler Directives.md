### What are Assembler Directives?

**Assembler directives** (also called **pseudo-instructions**) are **instructions given to the assembler**, not to the CPU.  
They **do not generate machine code**, but they **guide the assembler** in organizing memory, defining data, and controlling the assembly process.

---

## Common Assembler Directives (IMPORTANT)

---

## 1️⃣ `.data` Directive

### Purpose:

- Specifies the **data segment** of the program.
- Used to declare **variables and constants**.

### Example:

```
.data  
num: .word 10
```

📌 Meaning:

- Data following `.data` is stored in memory as **data**, not instructions.

---

## 2️⃣ `.text` Directive

### Purpose:

- Specifies the **code (instruction) segment**.
- All executable instructions are written here.

### Example:

```
.text  
main:  
  add $t0, $t1, $t2
```

📌 Meaning:

- Assembler treats following lines as **machine instructions**.

---

## 3️⃣ `.word` Directive ⭐ VERY IMPORTANT

### Purpose:

- Allocates **one or more words** (usually 32 bits) in memory.
- Initializes them with given values.

### Example:

```
.word 25  
.word 10, 20, 30
```

📌 Notes:

- Each `.word` occupies **4 bytes**
- Stored in **consecutive memory locations**

---

## 4️⃣ `.byte` Directive ⭐ IMPORTANT

### Purpose:

- Allocates **one or more bytes** (8 bits).
- Used for characters or small values.

### Example:

```
.byte 65  
.byte 1, 2, 3
```

📌 ASCII example:

.byte 'A'

👉 `'A'` is stored as **65 (ASCII)**.

---

## 5️⃣ `.half` Directive

### Purpose:

- Allocates **half-word (16-bit)** data.

### Example:

```
.half 100
```

📌 Occupies **2 bytes**.

---

## 6️⃣ `.asciiz` Directive

### Purpose:

- Stores a **null-terminated string**.
- Automatically adds `\0` at the end.

### Example:

```
.asciiz "Hello"
```

📌 Memory:

```
H e l l o \0
```
---

## 7️⃣ `.ascii` Directive

### Purpose:

- Stores a string **without null termination**.

### Example:

```
.ascii "Hello"
```

📌 Difference from `.asciiz`:

- ❌ No `\0` at the end

---

## 8️⃣ `.space` Directive

### Purpose:

- Reserves memory **without initialization**.

### Example:

```
.space 20
```

📌 Meaning:

- Reserves **20 bytes** of memory.

---

## 9️⃣ `.globl` Directive

### Purpose:

- Makes a label **globally accessible** (usually for main).

### Example:

```
.globl main
```

📌 Required for program entry point.

---

## Memory Layout View (Nice for Explanation ✍️)

```
.text   → Instructions  
.data   → Initialized data  
.heap   → Dynamic memory  
.stack  → Function calls
```