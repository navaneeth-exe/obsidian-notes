## 🎯 **AIM**

To write a program to determine whether the system is in a **safe state** using Banker’s Algorithm and to find the **safe execution sequence** of processes.

---

## 📚 **THEORY**

Banker’s Algorithm is a **deadlock avoidance algorithm** used in operating systems.

- It ensures that the system never enters an unsafe state
- Before allocating resources, it checks if the system remains safe

### 🔹 Key Data Structures:

- **Allocation[n][m]** → resources currently allocated
- **Max[n][m]** → maximum demand
- **Need[n][m]** → remaining need
    
    Need = Max - Allocation
    
- **Available[m]** → available resources

---

### 🔹 Safe State

A system is safe if there exists a sequence such that:

> All processes can complete without deadlock

---

### 🔹 Working Principle

- Try to find a process whose needs can be satisfied
- Execute it → release resources
- Repeat until all processes finish

---

# **Algorithm – Banker’s Algorithm (Using Work Array)**

### **Step 1: Input**

1. Read number of processes `n`
2. Read number of resource types `m`
3. Input:
    - Allocation matrix `alloc[n][m]`
    - Maximum matrix `max[n][m]`
    - Available vector `avail[m]`

---

### **Step 2: Calculate Need Matrix**

4. For each process `i` and each resource `j`:
    
    need[i][j] = max[i][j] - alloc[i][j]
    

---

### **Step 3: Initialize Variables**

5. Initialize:
    - `finish[i] = 0` for all processes
    - `count = 0`
6. Copy:
    
    work[j] = avail[j]
    

---

### **Step 4: Find Safe Sequence**

7. Repeat while `count < n`:
    - Set `found = 0`
8. For each process `i`:
    - If `finish[i] == 0`:
        a. Check if process can execute:
	        for all `j`: `need[i][j] <= work[j]`
        b. If yes:
        
        - Add allocated resources back:
            
            work[j] = work[j] + alloc[i][j]
            
        - Store process in safe sequence:
            
            safeSeq[count++] = i
            
        - Mark process as finished:
            
            finish[i] = 1
            
        - Set `found = 1`

---

### **Step 5: Deadlock Check**

9. If no process is found in a loop (`found == 0`):
    - Print:
        
        System is NOT in a safe state
        
    - Exit

---

### **Step 6: Safe State**

10. If all processes are finished:

- Print:
    
    System is in a SAFE STATE
    
- Display safe sequence

---

```
#include <stdio.h>

int main() {
    int n, m;
    int alloc[10][10], max[10][10], avail[10];
    int need[10][10], finish[10] = {0};
    int safeSeq[10];
    int work[10];   // NEW: work array

    int i, j, k, count = 0;

    printf("Enter the number of processes: ");
    scanf("%d", &n);

    printf("Enter the number of resource types: ");
    scanf("%d", &m);

    printf("\nEnter the Allocation Matrix (%d x %d):\n", n, m);
    for (i = 0; i < n; i++)
        for (j = 0; j < m; j++)
            scanf("%d", &alloc[i][j]);

    printf("\nEnter the Max Matrix (%d x %d):\n", n, m);
    for (i = 0; i < n; i++)
        for (j = 0; j < m; j++)
            scanf("%d", &max[i][j]);

    printf("\nEnter the Available Resources (vector of %d values):\n", m);
    for (j = 0; j < m; j++)
        scanf("%d", &avail[j]);

    // Calculate Need matrix
    for (i = 0; i < n; i++)
        for (j = 0; j < m; j++)
            need[i][j] = max[i][j] - alloc[i][j];

    // Copy Available to Work
    for (j = 0; j < m; j++)
        work[j] = avail[j];

    // Display Need matrix
    printf("\nNeed Matrix:\n");
    for (i = 0; i < n; i++) {
        for (j = 0; j < m; j++)
            printf("%3d ", need[i][j]);
        printf("\n");
    }

    // Banker's Algorithm
    while (count < n) {
        int found = 0;

        for (i = 0; i < n; i++) {
            if (finish[i] == 0) {

                int flag = 0;
                for (j = 0; j < m; j++) {
                    if (need[i][j] > work[j]) {
                        flag = 1;
                        break;
                    }
                }

                if (flag == 0) {
                    // process can execute
                    for (k = 0; k < m; k++)
                        work[k] += alloc[i][k];   // CHANGED: using work

                    safeSeq[count++] = i;
                    finish[i] = 1;
                    found = 1;
                }
            }
        }

        if (!found) {
            printf("\nSystem is NOT in a safe state (Deadlock possible)\n");
            return 0;
        }
    }

    // Safe sequence found
    printf("\nSystem is in a SAFE STATE.\n");
    printf("Safe Sequence: < ");
    for (i = 0; i < n; i++)
        printf("P%d ", safeSeq[i]);
    printf(">\n");

    return 0;
}
```


---
# **DETAILED CODE EXPLANATION – BANKER’S ALGORITHM**

---

## 🔹 **HEADER FILE**

```
#include <stdio.h>
```

👉 Used for input/output (`printf`, `scanf`)

---

# 🧱 **VARIABLE DECLARATION**

```
int n, m;  
int alloc[10][10], max[10][10], avail[10];  
int need[10][10], finish[10] = {0};  
int safeSeq[10];  
int work[10];
```

### Meaning of each:

- `n` → number of processes
- `m` → number of resource types

---

### 🔹 Matrices

- `alloc[i][j]` → resources currently allocated to process i
- `max[i][j]` → maximum resources needed

---

### 🔹 Vectors

- `avail[j]` → available resources
- `work[j]` → **temporary copy of available (VERY IMPORTANT)**

---

### 🔹 Other arrays

- `need[i][j]` → remaining need
- `finish[i]` → process completed or not
- `safeSeq[]` → stores safe execution order

---

# 📥 **INPUT SECTION**

```
scanf("%d", &n);  
scanf("%d", &m);
```
👉 Input number of processes and resources

---

### 🔹 Allocation Matrix Input

```
scanf("%d", &alloc[i][j]);
```

---

### 🔹 Max Matrix Input

```
scanf("%d", &max[i][j]);
```

---

### 🔹 Available Resources

```
scanf("%d", &avail[j]);
```

---

# 🧮 **NEED MATRIX CALCULATION**

```
need[i][j] = max[i][j] - alloc[i][j];
```

👉 Core formula:

```
Need = Max - Allocation
```

💡 Meaning:

> How many more resources each process still needs

---

# ⚠️ **IMPORTANT PART – WORK ARRAY**

```
for (j = 0; j < m; j++)  
    work[j] = avail[j];
```

👉 WHY THIS EXISTS:

- `work[]` is a **copy of available**
- We modify `work`, NOT original `avail`

💀 Examiner WILL ask this:

> “Why not use avail directly?”

👉 Answer:

> “To preserve original resource values, we use work as a temporary variable.”

---

# 🖨️ **PRINT NEED MATRIX**

```
printf("%3d ", need[i][j]);
```
👉 Just for display (not part of logic)

---

# 🔁 **MAIN LOOP (BANKER’S LOGIC)**

```
while (count < n)
```

👉 Loop runs until all processes finish

---

## 🔍 **FIND SAFE PROCESS**

```
if (finish[i] == 0)
```

👉 Only check unfinished processes

---

### 🔹 CONDITION CHECK

```
if (need[i][j] > work[j])
```

👉 If process needs more than available → cannot run

---

### 🔹 FLAG LOGIC

```
flag = 1;
```

👉 Means process cannot execute

---

## ✅ **IF PROCESS CAN EXECUTE**

```
if (flag == 0)
```

👉 Means:

```
Need <= Work
```
`
---

# 🔄 **RESOURCE ALLOCATION (SIMULATION)**

```
for (k = 0; k < m; k++)  
    work[k] += alloc[i][k];
```

👉 What happens:

- Process finishes
- Releases its resources
- Resources added back to `work`

💡 Example:
``
  
New Work = [4,2,3]

---

## 🔹 UPDATE STATE

```
safeSeq[count++] = i;  
finish[i] = 1;  
found = 1;
```

- Add process to safe sequence
- Mark as completed
- `found = 1` → progress happened

---

# 🚨 **UNSAFE STATE CHECK**

```
if (!found)
```

👉 If no process can execute:

```
printf("System is NOT in a safe state");

```
💀 Meaning:

> Deadlock may occur

---

# 🧾 **SAFE STATE OUTPUT**

```
printf("Safe Sequence: < ");

printf("P%d ", safeSeq[i]);
```

👉 Displays execution order

---

# 📤 **EXAMPLE INPUT**

```
Enter the number of processes: 5  
Enter the number of resource types: 3  
  
Enter the Allocation Matrix (5 x 3):  
0 1 0  
2 0 0  
3 0 2  
2 1 1  
0 0 2  
  
Enter the Max Matrix (5 x 3):  
7 5 3  
3 2 2  
9 0 2  
2 2 2  
4 3 3  
  
Enter the Available Resources (vector of 3 values):  
3 3 2
```

---

# 📊 **CALCULATED NEED MATRIX**

```
Need Matrix:  
 7  4  3  
 1  2  2  
 6  0  0  
 0  1  1  
 4  3  1
```

---

# ✅ **OUTPUT**

```
System is in a SAFE STATE.  
Safe Sequence: < P1 P3 P4 P0 P2 >
```

---
## ✅ **RESULT**

The Banker’s Algorithm was successfully implemented and the system was verified to be in a safe state with a valid safe sequence.

---

# 🔥 **VIVA QUESTIONS**

## 🧠 Basic

1. What is Banker’s Algorithm?  
    👉 Deadlock avoidance algorithm
2. What is safe state?  
    👉 All processes can complete

---

## ⚙️ Conceptual

3. What is Need matrix?  
    👉 Remaining resource requirement
4. Formula for Need?  
    👉 Need = Max – Allocation

---

## 🧮 Technical

5. What is Work variable?  
    👉 Copy of available resources
6. What is Finish array?  
    👉 Tracks completed processes

---

## 💀 Advanced

7. What is unsafe state?  
    👉 No safe sequence exists
8. Does unsafe always mean deadlock?  
    👉 No, but deadlock is possible
9. Time complexity?  
    👉 O(n² × m)

---

## 🧠 PRO LINE 😎

> “Banker’s algorithm checks for safe allocation by ensuring all processes can complete without causing deadlock.”