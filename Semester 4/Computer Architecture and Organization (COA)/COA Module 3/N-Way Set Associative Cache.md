# N-Way Set Associative Cache

## Definition

An **N-way set associative cache** is a cache organization in which the cache is divided into **multiple sets**, and **each set contains N blocks (ways)**.

Each memory address **maps to exactly one set**, but the data can be placed in **any of the N blocks within that set**.


---

# Basic Idea

In this cache organization:
- Cache is divided into **S sets**
- Each set contains **N blocks (ways)**
- A memory block maps to **one specific set**
- But it can occupy **any block within that set**

Here **N is called the degree of associativity**.


Example:
- **1-way set associative** → Direct mapped cache
- **2-way set associative** → Each set has 2 blocks
- **4-way set associative** → Each set has 4 blocks

---

# Cache Structure

Important terms:
- **C** = Cache capacity
- **b** = Block size
- **B = C / b** → Number of blocks
- **N** = Associativity (blocks per set)
- **S = B / N** → Number of sets

Each set stores:
- Data block
- Tag
- Valid bit


---

# Address Structure

For a **2-way set associative cache**:

- Set bits = **log₂(S)**

Example:

$$
log2(4)=2
$$

So address fields become:
```
Tag | Set Index | Byte Offset
```

Tag bits increase because fewer bits are used for the set index.


---

# Working of N-Way Set Associative Cache

1. CPU sends memory address.
2. **Set index bits select a cache set**.
3. All **N blocks in that set are read simultaneously**.
4. Their **tags are compared** with the address tag.
5. If a tag matches and valid bit = 1 → **Cache Hit**.
6. A **multiplexer selects the correct block**.
7. If no tag matches → **Cache Miss**, and the block is loaded into one of the ways.
    
    

---

# Advantages

- Reduces **conflict misses** compared to direct mapped cache.
- More flexible placement of data.

---

# Disadvantages

- More complex hardware
- Slower than direct mapped cache
- Requires multiple tag comparisons and multiplexers