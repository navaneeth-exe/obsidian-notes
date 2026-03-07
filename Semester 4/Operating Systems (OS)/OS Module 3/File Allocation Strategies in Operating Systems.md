File allocation strategies define **how disk blocks are allocated to store files on secondary storage**. The operating system uses different allocation methods to store and access files efficiently.

The three main file allocation methods are:
1. **Contiguous Allocation**
2. **Linked Allocation**
3. **Indexed Allocation**

---

# 1. Contiguous Allocation

### Definition

In **contiguous allocation**, each file occupies **continuous blocks on the disk**. The blocks of a file are stored next to each other.

Example:
```
File A → Blocks 10, 11, 12, 13  
File B → Blocks 14, 15
```

The directory entry stores:
- **Starting block address**
- **Length of the file**

---

### Advantages

- Simple implementation
- Fast **sequential access**
- Fast **direct access**

---

### Disadvantages

- **External fragmentation** occurs
- File size must be known beforehand
- Difficult to expand the file

---

# 2. Linked Allocation

### Definition

In **linked allocation**, file blocks are **scattered anywhere on the disk**, and each block contains a **pointer to the next block**.

Example:
```
Block 7 → Block 21 → Block 3 → Block 18
```

The directory stores the **address of the first block** of the file.

---

### Advantages

- **No external fragmentation**
- Files can grow easily
- Efficient use of disk space

---

### Disadvantages

- **Slow random access**
- Extra memory needed for pointers
- If a pointer is lost, the rest of the file cannot be accessed

---

# 3. Indexed Allocation

### Definition

In **indexed allocation**, each file has an **index block** that contains the addresses of all disk blocks of that file.

Example:
```
Index Block
-----------
9
16
1
10
25
```

Each entry points to a block containing file data.

---

### Advantages

- Supports **direct access**
- No external fragmentation
- Easy file expansion

---
### Disadvantages

- Extra space required for the index block
- Index block overhead for small files


---


Module : [[OS Module 3]]