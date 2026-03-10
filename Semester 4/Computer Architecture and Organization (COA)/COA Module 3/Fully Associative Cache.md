## Definition

A **Fully Associative Cache** is a cache organization in which **all cache blocks belong to a single set**, and a **memory block can be placed in any cache block**.

Thus, **any memory address can map to any cache block**.

---

# Basic Idea

In this cache organization:

- The cache contains **only one set**
- The set contains **B blocks (ways)**
- A memory block can be stored **in any block of the cache**

It is also called:
**B-way set associative cache with one set**.


---

# Working of Fully Associative Cache

When the processor requests data:
1. The address tag is **compared with all cache block tags**.
2. If any tag matches and **valid bit = 1**, a **cache hit occurs**.
3. The correct data block is selected using a **multiplexer**.
4. If no tag matches → **cache miss**, and the data is fetched from main memory.

For example, if there are **8 cache blocks**, then **8 tag comparisons** must be performed.

---

# Advantages

- **Fewest conflict misses**
- Highest flexibility in block placement
- Better cache utilization

---

# Disadvantages

- Requires **many comparators**
    
- Needs a **large multiplexer**
    
- More complex and expensive hardware
    

---

# Replacement Policy

Since any block can be placed anywhere, when the cache is full the system must decide **which block to replace**.

Common replacement policy:

**LRU (Least Recently Used)** – the block that has not been used for the longest time is replaced.