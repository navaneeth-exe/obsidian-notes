### ✔️ Logic

NAND = NOT(AND)

$$
A (NAND) B=A∧B
$$

So:

1. First do AND
2. Then invert result using XORI with -1 (all bits = 1)

---

### ✔️ RISC-V Code

```
AND  x5, x1, x2      # x5 = x1 AND x2  
XORI x5, x5, -1      # x5 = NOT(x5) → NAND result
```
---

### ✔️ Justification (write this in exam ✍️)

NAND operation is the complement of AND.  
First, AND instruction computes A∧BA \land BA∧B.  
Then XORI with immediate -1 inverts all bits because -1 in RISC-V is represented as all 1s in two’s complement.  
XOR with 1 flips each bit, producing NOT of the AND result.  
Hence, NAND is achieved.

---

# ✅ NOR using OR + XORI

### ✔️ Logic

NOR = NOT(OR)

$$
A (NOR) B=A∨B
$$

So:

1. First OR
2. Then invert using XORI -1

---

### ✔️ RISC-V Code

```
OR   x5, x1, x2      # x5 = x1 OR x2  
XORI x5, x5, -1      # x5 = NOT(x5) → NOR result
```

---

### ✔️ Justification (exam-ready ✍️)

NOR is the complement of OR.  
First, OR instruction computes A∨BA \lor BA∨B.  
Then XORI with -1 flips all bits of the result since -1 has all bits set to 1.  
This produces the bitwise NOT of the OR result.  
Therefore, NOR is implemented.