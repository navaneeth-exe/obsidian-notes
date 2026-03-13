## Definition

A **K-Dimensional Tree (K-d Tree)** is a **binary tree used to organize points in k-dimensional space**. It is a type of **spatial data structure** used for storing and searching **multi-dimensional data such as coordinates**.

Here **k represents the number of dimensions** of the data.

Example:

- 2D space → (x, y)
- 3D space → (x, y, z)
    

K-d trees are commonly used in **spatial searching problems**, such as finding nearby points or performing range searches.

---

# Construction of K-d Tree

The K-d tree is constructed by **recursively dividing the space into regions** using different dimensions.

### 1. First Level Split

The **first level splits the space using the first dimension (x-coordinate).**

All points are compared based on their **x value**, and a **median point** is usually chosen as the root.

Points with **smaller x values go to the left subtree**, and points with **larger x values go to the right subtree**.

---

### 2. Second Level Split

The **second level splits the space using the second dimension (y-coordinate).**

At this level, the nodes divide the points according to their **y values**.

Points with **smaller y values go to the left**, and points with **larger y values go to the right**.

---

### 3. Alternating Dimensions

The **splitting alternates between dimensions at each level.**

Example for a 2D tree:

- Level 0 → split using **x**
    
- Level 1 → split using **y**
    
- Level 2 → split using **x**
    
- Level 3 → split using **y**
    

This alternating process continues until all points are inserted.

---

### 4. Nodes in the Tree

Each **node represents a point in k-dimensional space**.

Example node:

```
(30, 40)
```

This represents a point where:

- x = 30
    
- y = 40
    

Each node also represents a **splitting line (or hyperplane)** that divides the space into two regions.

---

### 5. Recursive Space Division

The **tree recursively divides the space into smaller regions**.

Each node splits the space into **two parts**, and the process continues for the subtrees.

This hierarchical division allows **efficient searching of spatial data**.

---

# Example of a 2D K-d Tree

Points:

```
(30,40) (5,25) (10,12) (70,70) (50,30) (35,45)
```

Construction:

```
           (30,40)   ← split by x  
          /       \  
     (5,25)       (70,70)  
     split y      split y  
       /             /  
   (10,12)       (50,30)  
                    /  
                (35,45)
```

Each level **alternates between x and y comparisons**.

---

# Operations in K-d Tree

1. **Insertion**
    
    - Insert points by comparing coordinates based on the current dimension.
        
2. **Search**
    
    - Used to find whether a point exists in the tree.
        
3. **Range Search**
    
    - Finds all points within a given region.
        
4. **Nearest Neighbor Search**
    
    - Finds the closest point to a given query point.
        

---

# Advantages of K-d Tree

- Efficient storage of **multi-dimensional data**
    
- Faster **range queries**
    
- Useful for **nearest neighbor searching**
    

---

# Applications

- **Computer graphics**
    
- **Geographic Information Systems (GIS)**
    
- **Machine learning**
    
- **Database spatial indexing**