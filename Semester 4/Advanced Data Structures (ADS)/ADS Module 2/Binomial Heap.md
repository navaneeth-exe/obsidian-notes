A **Binomial Heap** is a collection of **binomial trees** that satisfy the **heap property**.

In a binomial heap, each binomial tree follows the **min-heap property**, meaning the **key of a parent node is less than or equal to the keys of its children**.

To get a **binomial heap**, connect the **roots of binomial trees**.

Point the **min pointer** to the root with the **lowest value in the root list**. That node is declared as the **root of the heap**.

There will be **at most one binomial tree of any order** in a binomial heap.


![[Pasted image 20260314002006.png]]
---

# Binomial Tree

A **binomial tree of order k (Bk)** is defined recursively.

- A **binomial tree of order 0 (B₀)** consists of a **single node**.
    
- A **binomial tree of order k** is formed by **linking two binomial trees of order (k-1)**, where **one becomes the leftmost child of the other**.
    
- A **binomial tree of order 0 contains only one node**.
    

---

# Operations on Binomial Heap

## 1. Insertion

Consider the node to be inserted as a **binomial heap itself**.

Then perform the **union operation** with the **original heap**.

---

## 2. Extract Minimum

Removes the **node with the minimum key** from the heap.

The children of the removed node are **reversed and merged** with the remaining heap.

---

## 3. Get Minimum

Return the **minimum value** from the heap.

The minimum element is found by **checking the root list**.

---

## 4. Union

Union operation **merges two binomial heaps**.

### Steps

1. Merge the **root lists** of the two heaps.
    
2. Traverse the root list of the merged heap.
    
3. Maintain **three pointers**:
    
    - Previous node
        
    - Current node
        
    - Next node
        
---
# Conditions During Union

### Case 1

If **current node and next node have different degrees**,  
move forward in the list.

### Case 2

If **current node and next node have the same degree**:

1. If the **current node has a smaller key than the next node**,  
    make the **next node the child of the current node**.
    
2. Otherwise,  
    make the **current node the child of the next node**.
    

If **three consecutive trees have the same degree**,  
move forward without linking.

---

# Time Complexity

|Operation|Time Complexity|
|---|---|
|Create Heap|O(1)|
|Insertion|O(log n)|
|Extract Minimum|O(log n)|
|Union|O(log n)|
|Deletion|O(log n)|