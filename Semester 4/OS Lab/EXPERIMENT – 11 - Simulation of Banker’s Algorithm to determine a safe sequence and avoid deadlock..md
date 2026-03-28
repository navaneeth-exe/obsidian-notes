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

# 🧾 **ALGORITHM**

**Step 1:** Input:

- Number of processes `n`
- Number of resources `m`
- Allocation matrix
- Max matrix
- Available vector

---

**Step 2:** Compute Need matrix:

Need[i][j] = Max[i][j] - Allocation[i][j]

---

**Step 3:** Initialize:

- `Work = Available`
- `Finish[i] = False`

---

**Step 4:** Find process `Pi` such that:

Need[i][j] <= Work[j] for all j

---

**Step 5:** If found:

- Add process to safe sequence
- Update:

Work = Work + Allocation[i]  
Finish[i] = True

---

**Step 6:** Repeat until:

- All processes finish OR
- No process satisfies condition

---

**Step 7:**

- If all `Finish[i] = True` → SAFE STATE
- Else → UNSAFE STATE