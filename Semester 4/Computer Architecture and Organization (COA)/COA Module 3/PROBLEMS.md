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

22
$$
Miss Rate=210Miss\ Rate = \frac{2}{10}Miss Rate=102​ Miss Rate=0.2=20%Miss\ Rate = 0.2 = 20\%Miss Rate=0.2=20%
$$

---

# Final Answer

- Misses = **2**
    
- Total accesses = **10**
    

Miss Rate = 20%\textbf{Miss Rate = 20\%}Miss Rate = 20%