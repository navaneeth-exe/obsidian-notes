
## Definition

**Cache mapping** is the process of determining **how blocks of main memory are placed into cache memory**.

Since **cache memory is much smaller than main memory**, only some memory blocks can be stored in cache at a time. Cache mapping decides **where a particular main memory block should be stored in cache**.

---

## Why Cache Mapping is Needed

Main memory is **very large**, but cache memory is **very small**.

Example:

| Memory Type  | Size  |
| ------------ | ----- |
| Main Memory  | 16 GB |
| Cache Memory | 8 MB  |

So obviously **all memory blocks cannot fit into cache**.

Because of this, the system needs a **rule or technique** to decide:
- Which block goes into cache
- Where it should be stored in cach 

That rule is called **cache mapping**.

---

## What Happens During Cache Mapping

When the CPU requests data:

1. CPU generates a **memory address**.
2. Cache checks whether the data is already stored.
3. Mapping technique determines **which cache location should contain that memory block**.
4. If data is found → **[[Hit Rate & Miss Rate|Cache Hit]]**
5. If data is not found → **[[Hit Rate & Miss Rate|Cache Miss]]**, data is fetched from main memory.


















Modul