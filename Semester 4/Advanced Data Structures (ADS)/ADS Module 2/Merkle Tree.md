A **Merkle Tree** is a hierarchical tree structure used to **efficiently verify and summarize large sets of data**.  
In this structure, **data blocks are stored at the leaf nodes**, and each node contains a **cryptographic hash** of its children.  
The topmost node is called the **Merkle Root**, which represents the hash of the entire dataset.

If any data in the tree changes, the corresponding hashes also change, which eventually changes the **Merkle Root**, allowing easy detection of data tampering.

---

# Construction of a Merkle Tree

The construction of a Merkle tree follows these steps:

### 1. Data Division

The dataset is divided into smaller blocks.  
```
Example: Data A, Data B, Data C, Data D.
```

### 2. Leaf Hashing

Each data block is passed through a **hash function** to generate leaf nodes.

```
Hash A = H(Data A)  
Hash B = H(Data B)  
Hash C = H(Data C)  
Hash D = H(Data D)
```

### 3. Pairing and Hashing

Adjacent hashes are combined and hashed again to create **intermediate nodes**.

```
Hash AB = H(Hash A + Hash B)  
Hash CD = H(Hash C + Hash D)
```

### 4. Root Formation

The intermediate hashes are again combined to produce the **Merkle Root**.

```
Merkle Root = H(Hash AB + Hash CD)
```

---

# Structure of a Merkle Tree

        Merkle Root (Hash ABCD)  
             /        \  
        Hash AB      Hash CD  
        /    \        /    \  
     Hash A Hash B Hash C Hash D  
        |      |      |      |  
      Data A Data B Data C Data D

If the number of data blocks is **odd**, the last hash may be **duplicated** so that every node has a pair.

---

# Operations on Merkle Tree

## 1. Verification

Used to check whether a specific data block belongs to the tree.

**Process:**

- Use the **authentication path** (sibling hashes).
    
- Combine hashes from leaf to root.
    
- If the computed root equals the stored **Merkle Root**, the data is valid.
    

**Time Complexity:**  
```
O(log N)
```

---

## 2. Update

When a leaf node changes:

**Process:**

1. Recalculate the hash of the modified leaf.
    
2. Update hashes along the path to the root.
    

Only the affected path is updated.

**Time Complexity:**  
```
O(log N)
```

---

## 3. Insertion

When new data is added:

**Process:**

- Insert a new leaf node.
    
- Recalculate hashes upward.
    
- A new **Merkle Root** is generated.
    

---

## 4. Deletion

When a leaf node is removed:

**Process:**

- Remove the node.
    
- Adjust the tree structure.
    
- Recalculate hashes up to the root.
    

Deletion is less common in applications like blockchain.

---

# Applications of Merkle Tree

Merkle trees are widely used in:

- **Blockchain**
    
- Distributed systems
    
- Data integrity verification
    
- Peer-to-peer networks