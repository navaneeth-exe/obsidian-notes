# 1. FCFS (First Come First Serve)

### Definition

Requests are processed **in the order they arrive**.

Example queue:

```
98 → 183 → 37 → 122
```

### Advantages

- Simple and fair
- Easy to implement

### Disadvantages

- Large head movement
- Poor performance

---

# 2. SSTF (Shortest Seek Time First)

### Definition

The request **closest to the current head position** is serviced first.

### Advantages

- Reduces seek time
- Better performance than FCFS

### Disadvantages

- Possibility of **starvation**
- Requests far away may wait long

---

# 3. SCAN (Elevator Algorithm)

### Definition

The disk arm moves **in one direction servicing requests**, then reverses direction.

Movement example:
```
0 → 199 → 0
```
### Advantages

- Better performance than SSTF
- Less starvation

### Disadvantages

- Some requests wait longer

---

# 4. C-SCAN (Circular SCAN)

### Definition

The disk head moves **only in one direction**.  
After reaching the end, it **returns to the beginning without servicing requests**.

Example movement:
```
0 → 199 → jump → 0
```

### Advantages

- Provides **uniform waiting time**
### Disadvantages

- Extra head movement due to jump

---

# 5. LOOK

### Definition

Similar to SCAN but the disk head **only goes as far as the last request**, not the end of the disk.

### Advantages

- Reduces unnecessary movement

### Disadvantages

- Slightly complex

---

# 6. C-LOOK

### Definition

Similar to C-SCAN but the head **moves only up to the last request before jumping back**.

### Advantages

- Efficient movement
- Uniform waiting time

### Disadvantages

- Implementation complexity


## Comparison of Disk Scheduling Algorithms 

| Algorithm                           | Basic Idea                                                          | Head Movement | Starvation | Performance              |
| ----------------------------------- | ------------------------------------------------------------------- | ------------- | ---------- | ------------------------ |
| **FCFS (First Come First Serve)**   | Requests are serviced in the order they arrive                      | High          | No         | Poor                     |
| **SSTF (Shortest Seek Time First)** | Selects request closest to current head position                    | Low           | Possible   | Better than FCFS         |
| **SCAN (Elevator Algorithm)**       | Disk arm moves in one direction servicing requests, then reverses   | Medium        | Rare       | Good                     |
| **C-SCAN (Circular SCAN)**          | Head moves in one direction only and jumps back to start            | Medium        | No         | Better uniform wait time |
| **LOOK**                            | Similar to SCAN but moves only up to last request                   | Less          | Rare       | Better than SCAN         |
| **C-LOOK**                          | Similar to C-SCAN but goes only to last request before jumping back | Least         | No         | Best performance         |

---


Module : [[OS Module 3]]