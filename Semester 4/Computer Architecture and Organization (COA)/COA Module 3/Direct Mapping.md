
Module : [[COA Module 3]]


## Definition

**Direct Mapping** is a cache mapping technique in which **each block of main memory is mapped to exactly one specific cache line**.

So basically:  
👉 One memory block → **only one fixed cache location**.

The mapping is done using a **modulo function**.

$$
Cache Line=(Memory Block Number)\ mod\ (Number of Cache Lines)
$$

---

# Structure of Address in Direct Mapping

A memory address is divided into **three parts**:

1. **Tag**
2. **Index (Cache Line)**
3. **Block Offset**

Example format:

```
| TAG | INDEX | OFFSET |
```

### Meaning

|Field|Purpose|
|---|---|
|Tag|Identifies which memory block is stored|
|Index|Selects cache line|
|Offset|Selects data inside the block|

---

# Working of Direct Mapping

1. CPU generates a **memory address**.
2. The **Index bits** determine which **cache line** to check. 
3. The **Tag** stored in that cache line is compared with the address tag.
4. If they match → **Cache Hit**
5. If they don't match → **Cache Miss**, block is fetched from main memory.

---

# Example

Assume:
- Cache lines = **8**
- Memory blocks = **32**

Mapping formula:
$$
Cache Line=Block Number\mod \ 8
$$

Example mappings:

| Memory Block | Cache Line |
| ------------ | ---------- |
| 0            | 0          |
| 1            | 1          |
| 8            | 0          |
| 9            | 1          |
| 16           | 0          |

Notice something 👀

Blocks **0, 8, 16, 24** all map to **cache line 0**.

So if block 8 comes, it **replaces block 0**.

This causes **conflict misses**.

---

# Diagram (Simple)

```
Main Memory Blocks  
  
0   → Cache Line 0  
1   → Cache Line 1  
2   → Cache Line 2  
3   → Cache Line 3  
8   → Cache Line 0  
9   → Cache Line 1
```
Multiple memory blocks compete for the **same cache line**.

---

# Advantages

1. **Simple implementation**
2. **Fast access**
3. **Low hardware cost**

---

# Disadvantages

1. **High conflict misses**
2. Different blocks map to the same cache line
3. Poor cache utilization compared to associative mapping