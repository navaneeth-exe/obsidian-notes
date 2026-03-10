

# Example – Cache Block Conflict (Direct Mapped Cache)

## Given

- Cache type: **Direct mapped cache**
- Cache size: **8 words**
- Block size: **1 word**
- Cache initially **empty**
- Loop runs **5 times**

Code:

```
addi s0, zero, 5  
addi s1, zero, 0  
  
LOOP:  
beq s0, zero, DONE  
lw s2, 0x4(s1)  
lw s4, 0x24(s1)  
addi s0, s0, −1  
j LOOP  
  
DONE:
```

Each iteration performs **2 memory accesses**.

---

# Step 1 – Total Memory Accesses

Loop runs **5 times**

Each iteration:

lw s2, 0x4(s1)  
lw s4, 0x24(s1)

So:

$$
Total\ accesses=5×2=10
$$

---

# Step 2 – Find Cache Set for Each Address

Cache has **8 sets**.

Both addresses:
- **0x4**
- **0x24**

map to **Set 1**.

So:

|Address|Cache Set|
|---|---|
|0x4|Set 1|
|0x24|Set 1|

This happens because in a **direct mapped cache each address has only one possible cache location**.


---

# Step 3 – First Iteration

Cache is empty.

1️⃣ Access **0x4**
- Miss
- Stored in **Set 1**

2️⃣ Access **0x24**
- Maps to **same set (Set 1)**
- Replaces **0x4**

So now cache contains:

Set 1 → 0x24

---

# Step 4 – Second Iteration

1️⃣ Access **0x4**
- Not in cache
- Miss
- Replaces **0x24**

2️⃣ Access **0x24**
- Miss again
- Replaces **0x4**

This keeps happening every loop.

---

# Step 5 – What is Happening?

Both addresses compete for the **same cache block**.

This is called a:

**Cache Block Conflict (Conflict Miss)**

Each new access **evicts the previous block**.

---

# Step 6 – Miss Rate

Total accesses:

10

Misses:

10
$$
Miss Rate=10/10=100%
$$


---
# Example 8.8 – Set Associative Cache Miss Rate

## Given

- Cache size = **8 words**
- Cache type = **2-way set associative cache**
- Addresses accessed = **0x4 and 0x24**
- Loop runs **5 times**
- Each iteration performs **2 memory accesses**

Total accesses:

$$
5×2=10
$$

---

# Step 1 – Find the Cache Set

Both addresses:
```
0x4  
0x24
```
map to **Set 1**.

---

# Step 2 – First Loop Iteration

Cache is initially **empty**.

1. Access **0x4** → **Miss**
    - Stored in **Way 0 of Set 1**
2. Access **0x24** → **Miss**
    - Stored in **Way 1 of Set 1**

Because the cache has **two ways**, it can store **both addresses simultaneously**.

So after first iteration:

```
Set 1  
Way 0 → 0x4  
Way 1 → 0x24
```

---

# Step 3 – Remaining Iterations

Next **4 iterations** again access:

```
0x4  
0x24
```
Both are **already in cache**, so they result in **cache hits**.

Hits:

$$
4×2=8
$$

---

# Step 4 – Miss Rate

Total accesses
10

Misses:

2

$$
Miss Rate=2/10
$$

$$
 Miss Rate=0.2=20%
$$
---

# Final Answer

- Misses = **2**
- Total accesses = **10**

$$
Miss Rate = 20%\textbf{Miss Rate = 20\%}
$$