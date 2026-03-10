# N-Way Set Associative Cache

## Definition

An **N-way set associative cache** is a cache organization in which the cache is divided into **multiple sets**, and **each set contains N blocks (ways)**.

Each memory address **maps to exactly one set**, but the data can be placed in **any of the N blocks within that set**.

module 3 Complete notes

---

# Basic Idea

In this cache organization:

- Cache is divided into **S sets**
    
- Each set contains **N blocks (ways)**
    
- A memory block maps to **one specific set**
    
- But it can occupy **any block within that set**
    

Here **N is called the degree of associativity**.

memory system part 2

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

# Example (From Notes)

Given:

- Cache capacity **C = 8 words**
    
- Block size **b = 1 word**
    
- Associativity **N = 2**
    

Step 1: Number of blocks

B=C/b=8/1=8B = C/b = 8/1 = 8B=C/b=8/1=8

Step 2: Number of sets

S=B/N=8/2=4S = B/N = 8/2 = 4S=B/N=8/2=4

So the cache has:

- **4 sets**
    
- **Each set has 2 blocks (ways)**
    
    module 3 Complete notes
    

---

# Address Structure

For a **2-way set associative cache**:

- Set bits = **log₂(S)**
    

Example:

log2(4)=2 set bitslog_2(4) = 2 \text{ set bits}log2​(4)=2 set bits

So address fields become:

Tag | Set Index | Byte Offset

Tag bits increase because fewer bits are used for the set index.

module 3 Complete notes

---

# Working of N-Way Set Associative Cache

1. CPU sends memory address.
    
2. **Set index bits select a cache set**.
    
3. All **N blocks in that set are read simultaneously**.
    
4. Their **tags are compared** with the address tag.
    
5. If a tag matches and valid bit = 1 → **Cache Hit**.
    
6. A **multiplexer selects the correct block**.
    
7. If no tag matches → **Cache Miss**, and the block is loaded into one of the ways.
    
    module 3 Complete notes
    

---

# Advantages

- Reduces **conflict misses** compared to direct mapped cache.
    
- More flexible placement of data.
    

---

# Disadvantages

- More complex hardware
    
- Slower than direct mapped cache
    
- Requires multiple tag comparisons and multiplexers