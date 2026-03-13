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

Consider the following points in a 2-D plane:

(3,6), (17,15), (13,15), (6,12), (9,1), (2,7), (10,19)

In a **2-D tree**, the comparison **alternates between X and Y coordinates** at each level.

- Root → **X comparison**
    
- Next level → **Y comparison**
    
- Next → **X comparison**
    
- and so on.
    

---

# Step-by-Step Insertion

### 1. Insert (3, 6)

The tree is empty, so this point becomes the **root node**.

Root nodes are **X-aligned**, meaning comparisons will be done using **X values**.

```
(3,6)
```

---

### 2. Insert (17, 15)

Compare with root using **X-coordinate**.

```
17 > 3
```

So the point goes to the **right subtree**.

This node becomes **Y-aligned**.

```
        (3,6)  
           \  
        (17,15)
```

---

### 3. Insert (13, 15)

First compare with root using **X-coordinate**.

```
13 > 3
```

Move to the **right subtree**.

Now compare **Y-coordinate** with (17,15).

```
15 = 15
```

Equal values are placed in the **right subtree**.

This node becomes **X-aligned**.

```
        (3,6)  
           \  
        (17,15)  
              \  
           (13,15)
```

---

### 4. Insert (6, 12)

Compare with root using **X**.

```
6 > 3
```

Move right.

Compare with **(17,15) using Y**.

```
12 < 15
```

So it goes to the **left subtree**.

This node becomes **X-aligned**.

```
        (3,6)  
           \  
        (17,15)  
        /      \  
   (6,12)    (13,15)
```

---

### 5. Insert (9, 1)

Compare with root using **X**.

```
9 > 3
```

Move right.

Compare with (17,15) using **Y**.

```
1 < 15
```

Move left.

Compare with (6,12) using **X**.

```
9 > 6
```

So it goes to the **right of (6,12)**.
```
        (3,6)  
           \  
        (17,15)  
        /      \  
   (6,12)    (13,15)  
       \  
      (9,1)
```

---

### 6. Insert (2, 7)

Compare with root using **X**.

```
2 < 3
```

So it goes to the **left of (3,6)**.

```
           (3,6)  
          /     \  
      (2,7)   (17,15)  
              /      \  
         (6,12)    (13,15)  
            \  
            (9,1)
```

---

### 7. Insert (10, 19)

Compare with root using **X**.

```
10 > 3
```

Move right.

Compare with (17,15) using **Y**.

```
19 > 15
```

Move right.

Compare with (13,15) using **X**.

```
10 < 13
```

So it goes to the **left of (13,15)**.

```
           (3,6)  
          /     \  
      (2,7)   (17,15)  
              /      \  
         (6,12)    (13,15)  
            \        /  
            (9,1) (10,19)
```

---

# Final 2-D Tree

```
           (3,6)  
          /     \  
      (2,7)   (17,15)  
              /      \  
         (6,12)    (13,15)  
            \        /  
            (9,1) (10,19)
```

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