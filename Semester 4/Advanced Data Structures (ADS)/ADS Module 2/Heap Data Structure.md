## Definition

A **heap** is a **specialized tree-based data structure** that satisfies the **heap property**.  
It is a **complete binary tree** where each node follows a specific order with respect to its children.

A heap is mainly used to implement **Priority Queue** efficiently.

---

## Types of Heap

### 1. Max Heap

In a **Max Heap**, the value of each parent node is **greater than or equal to its children**.

Example:
```
        50
       /  \
     30    40
    / \    /
   10 20  35
```
Here the **largest element is always at the root**.

---

### 2. Min Heap

In a **Min Heap**, the value of each parent node is **less than or equal to its children**.

Example:
```
        10
       /  \
     20    15
    / \    /
   30 40  50
```
Here the **smallest element is always at the root**.

---

## Properties of Heap

1. **Complete Binary Tree**  
    All levels are completely filled except possibly the last level.
    
2. **Heap Order Property**
    
    - **Max Heap:** Parent ≥ Children
        
    - **Min Heap:** Parent ≤ Children
        
3. **Efficient Access**  
    The root element (minimum or maximum) can be accessed quickly.
    

---

## Array Representation of Heap

A heap is usually stored in an **array**.

If a node is at index **i**:

- Left child → `2i`
    
- Right child → `2i + 1`
    
- Parent → `i / 2`
    

Example array representation:

```
Index : 1  2  3  4  5  
Value :10 20 15 30 40
```

---

## Operations on Heap

### 1. Insertion

- Insert the element at the **end of the heap**.
    
- Adjust the heap using **heapify (bubble up)** to maintain the heap property.
    

Time Complexity: **O(log n)**

---

### 2. Deletion

- Remove the **root element**.
    
- Replace it with the **last element**.
    
- Apply **heapify (bubble down)**.
    

Time Complexity: **O(log n)**

---

### 3. Heapify

Heapify is the process of **rearranging elements to maintain the heap property**.

---

## Applications of Heap

- **Priority Queues**
    
- **Heap Sort**
    
- **Graph algorithms like Dijkstra's Algorithm**
    
- Scheduling systems