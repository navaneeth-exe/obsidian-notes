## Definition

A **Quad Tree** is a **spatial data structure used to store and organize two-dimensional spatial data**.

It works by **recursively dividing a 2-D space into four equal regions (quadrants)** until a condition is satisfied.

The four regions are:

- **North-West (NW)**
    
- **North-East (NE)**
    
- **South-West (SW)**
    
- **South-East (SE)**
    

Each node in a quad tree **represents a region of space**, and it can have **at most four children**.

---

# Working Principle

1. The **entire space is considered as the root node**.
    
2. If the **number of points in a region exceeds a maximum limit (N)**, the region is **divided into four equal quadrants**.
    
3. Each quadrant **stores the points that fall within its region**.
    
4. The division **continues recursively** until every region satisfies the condition.
    

---

# Example (Based on Diagram)

The 2D space ranges from **0 to 127** on both X and Y axes.

Points inserted:

|Point|Coordinates|
|---|---|
|A|(40,45)|
|B|(15,70)|
|C|(70,10)|
|D|(69,50)|
|E|(55,80)|
|F|(80,90)|

Assume the condition:

N = 1

This means **each region can contain only one point**.

---

# Step 1: Root Division

The entire space is the **root node**.

It is divided into **four quadrants**:

- **NW**
    
- **NE**
    
- **SW**
    
- **SE**
    

Now the points are placed according to their coordinates.

---

# Step 2: Insert First Points

### NW Quadrant

Point **A (40,45)** lies in the **North-West region**.

So **A is stored in NW**.

---

### SW Quadrant

Point **B (15,70)** lies in the **South-West region**.

So **B is stored in SW**.

---

### NE Quadrant

Points **C (70,10)** and **D (69,50)** both lie in the **North-East region**.

Since **two points exceed the limit N = 1**, this quadrant **must be subdivided again**.

---

### SE Quadrant

Points **E (55,80)** and **F (80,90)** lie in the **South-East region**.

Since **two points are present**, this region **must also be subdivided**.

---

# Step 3: Subdivision of NE Region

The **NE region splits into four smaller quadrants**.

Points inside this region:

- **C (70,10)**
    
- **D (69,50)**
    

They are placed into their respective sub-quadrants.

Now each sub-region satisfies the condition **N = 1**.

---

# Step 4: Subdivision of SE Region

The **SE region also splits into four sub-quadrants**.

Points inside:

- **E (55,80)**
    
- **F (80,90)**
    

These are placed in separate subregions.

---

# Resulting Quad Tree Structure

The quad tree looks like this:

https://opendsa-server.cs.vt.edu/ODSA/Books/CS3/html/_images/PRexamp.png

Each **internal node represents a region**, and **leaf nodes store the actual points**.

---

# Space Partitioning (From the Diagram)

The 2D space is divided like this:

1. First division → **4 main quadrants**
    
2. Regions containing **more than one point** are subdivided again.
    
3. Smaller quadrants continue forming until **each region contains only one point**.
    

This creates the **hierarchical grid shown in the diagram**.

[![Example of a PR quadtree](https://opendsa-server.cs.vt.edu/ODSA/Books/CS3/html/_images/PRexamp.png)](https://opendsa-server.cs.vt.edu/ODSA/Books/CS3/html/_images/PRexamp.png)

---

# Time Complexity

|Operation|Complexity|
|---|---|
|Search|**O(log N)** average|
|Insertion|**O(log N)**|
|Worst case|**O(N)**|

---

# Applications

Quad Trees are widely used in:

- **Geographic Information Systems (GIS)**
    
- **Image processing**
    
- **Computer graphics**
    
- **Collision detection in games**
    
- **Spatial indexing**