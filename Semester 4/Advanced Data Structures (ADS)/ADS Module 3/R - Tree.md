## Definition

An **R-tree** is a tree data structure used for indexing **spatial information** such as geographical coordinates, rectangles, and polygons.  
It is considered the **multi-dimensional equivalent of a B-tree**.

R-trees group nearby objects and represent them using **Minimum Bounding Rectangles (MBR)** so that spatial searching becomes efficient.

---

# 1. How it Divides Space

R-trees organize spatial objects hierarchically using **Minimum Bounding Rectangles (MBRs)**.

**Leaf Nodes:**  
Leaf nodes contain the actual spatial objects (such as points or polygons) along with their MBR.

**Internal Nodes:**  
Internal nodes store MBRs that cover all the rectangles of their child nodes.

As we move up the tree, the rectangles become larger until the **root node contains a single MBR covering the entire dataset**.

Unlike structures such as Quad-trees, **MBRs in an R-tree may overlap**, although the algorithm tries to minimize this overlap to improve search efficiency.

---

# 2. Structure Example

Consider several spatial objects **A, B, C, D, E**.

**Level 0 – Objects:**  
Individual spatial objects.

**Level 1 – Leaf MBRs:**  
Nearby objects are grouped into rectangles:  
R1 → contains objects A and B  
R2 → contains objects C, D, and E

**Level 2 – Root MBR:**  
R1 and R2 are grouped into a larger rectangle called the **Root**.

**Tree Representation**

```
Root Node  
 ├── R1  
 │     ├── Object A  
 │     └── Object B  
 └── R2  
       ├── Object C  
       ├── Object D  
       └── Object E
```
---

# 3. How a Search Works

To find an object at coordinate **(x, y)**:

1. Start at the **Root node** and check if the point lies inside the root MBR.
    
2. If it does, check the **child rectangles** (R1 and R2).
    
3. If the point is outside a rectangle, that branch is **ignored (pruned)**.
    
4. Continue searching in the rectangle that contains the point until the object is found.
    

This method greatly reduces the number of objects that must be checked.

---

# 4. Key Properties

• **Balanced:** All leaf nodes are at the same depth.

• **Dynamic:** Supports efficient insertion and deletion by splitting or merging nodes, similar to a B-tree.

• **Overlapping Rectangles:** Since rectangles can overlap, a search may sometimes follow multiple paths.

---

# R-Tree Example

Assume we have spatial objects **E, F, and G** located in a 2D space.

![[Pasted image 20260313233924.png|297]]![[Pasted image 20260313234001.png]]
### Step 1 – Objects

Small rectangles represent the **actual objects**.
- **E**
    
- **F**
    
- **G**
    

### Step 2 – First Level Rectangles

Nearby objects are grouped.

- **Rectangle B** contains **E**
    
- **Rectangle C** contains **F and G**
    

These are **first-level bounding rectangles**.

### Step 3 – Higher Level Rectangle

All rectangles are grouped again.

- **Rectangle A** covers **B, C, and D**
    

So **A is the root rectangle**.

---

# How it Divides the Space

The R-tree manages space using three main rules:

**1. Minimizing Overlap**  
The algorithm tries to reduce overlap between rectangles so searches remain efficient.

**2. Balancing**  
All leaf nodes are located at the same level, ensuring consistent search time.

**3. Expansion**  
When a new point is inserted, the corresponding rectangle expands slightly.  
If the rectangle becomes too full, it splits into two smaller rectangles.

---

# Why R-Tree is Better than a List

If there are **1,000,000 spatial objects**:

Instead of checking every object one by one,

1. Check the **Root rectangle**.
    
2. Check only relevant rectangles (such as R1 or R2).
    
3. Search only the objects inside that rectangle.
    

Thus, most of the data is ignored quickly, making the search **much faster**.

