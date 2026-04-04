	## **Definition**

Banker’s Algorithm is a **deadlock avoidance algorithm** used to allocate resources safely to processes.  
It checks whether the system can remain in a **safe state** after allocation.

A safe state means all processes can finish in some order (safe sequence).

---

# **Requirements of Banker’s Algorithm**

(Your note starts with this — so write this first ⭐)

Banker’s algorithm needs **3 things**:

1. **Initial Allocation**
2. **Maximum Need (Max demand)**
3. **Total Available Resources**

Using these, the algorithm allocates resources and generates a **safe execution sequence**.

---

# **Data Structures Used**

Let there be:

```
n processes
m resource types
```

---

## **1) Available Array**

`Avail[j]`

Represents currently available resources of each type.

---

## **2) Max Matrix**

`Max[i][j]`

Max[i][j] = maximum need of jth resource for ith process.

---

## **3) Need Matrix**

`Need[i][j]`

`Need[i][j] `= remaining need of jth resource for ith process.

Formula:

$$
Need[i][j]=Max[i][j]−Alloc[i][j]
$$

---

## **4) Allocation Matrix**

`Alloc[i][j]`

`Alloc[i][j] `= number of jth resources allocated to ith process.

---

## **5) Total Array**

`Total[j]`

Total resources of each type before allocation.

---

# **Algorithm to Allocate Resources & Check Safe State**


### **Step 1: Calculate Available**

$$
A[j]=Total[j]−∑Alloc[i][j]
$$

(Current available resources)

---

### **Step 2: Check Need ≤ Available**

Find a process Pi such that:

$$
Need[i][j]≤A[j]
$$

If yes → execute that process.

If not → check another process.

---

### **Step 3: Release Resources**

After process execution:

$$
A[j]=A[j]+Alloc[i][j]
$$

Process Pi is terminated.

---

### **Step 4: Repeat**

Repeat Step 2 and 3 for all processes.

---

### **Step 5: Safe Sequence**

- If all processes execute → **Safe State**
- Execution order is the **Safe Sequence**
- If some process cannot execute → **Unsafe State**