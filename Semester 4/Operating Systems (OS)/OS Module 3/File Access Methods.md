A **file access method** defines the way in which data stored in a file can be **read or written**. The operating system provides different methods so programs can access file data efficiently depending on the application.

Abraham-Silberschatz-Operating-…

The three common file access methods are:

1. **Sequential Access**
    
2. **Direct Access (Random Access)**
    
3. **Indexed Access**
    

---

# 1. Sequential Access

### Definition

In **sequential access**, records in a file are accessed **one after another in order** from the beginning to the end.

It is the **simplest and most common access method**.

---

### Working

- The file pointer moves **sequentially**.
    
- To access a record, all previous records must be read.
    

Example:

Record1 → Record2 → Record3 → Record4 → Record5

If the system needs **Record4**, it must read Record1, Record2, and Record3 first.

---

### Operations

Typical operations include:

- **read next**
    
- **write next**
    
- **reset pointer**
    
- **skip forward/backward**
    

---

### Advantages

- Simple to implement
    
- Efficient for **batch processing**
    
- Suitable for **magnetic tape storage**
    

---

### Disadvantages

- Slow for random access
    
- Cannot directly jump to a specific record
    

---

### Example Uses

- Text files
    
- Log files
    
- Backup systems
    

---

# 2. Direct Access (Random Access)

### Definition

In **direct access**, records can be **read or written in any order** without reading previous records.

Each record has a **relative address**.

---

### Working

The system directly accesses a specific record using its address.

Example:

Record1  Record2  Record3  Record4  Record5  
   ↑        ↑        ↑        ↑        ↑  
   0        1        2        3        4

If the system needs **Record3**, it directly accesses address **2**.

---

### Operations

Typical operations:

- **read(n)** → read record n
    
- **write(n)** → write record n
    

---

### Advantages

- Fast access to any record
    
- Efficient for **database systems**
    

---

### Disadvantages

- More complex than sequential access
    
- Requires **special hardware support**
    

---

### Example Uses

- Databases
    
- Disk-based file systems
    

---

# 3. Indexed Access

### Definition

In **indexed access**, a separate **index table** is maintained that contains pointers to records in the file.

The index helps locate the required record quickly.

---

### Working

The system first searches the **index**, then accesses the record.

Example:

Index Table  
A → Record1  
B → Record2  
C → Record3  
D → Record4

To access **Record3**, the system searches the index for **C**.

---

### Advantages

- Fast search and retrieval
    
- Supports both **sequential and direct access**
    

---

### Disadvantages

- Extra storage needed for the index
    
- Index maintenance overhead
    

---

### Example Uses

- Large databases
    
- Search systems
    
- File indexing systems



---

Module : [[OS Module 3]]