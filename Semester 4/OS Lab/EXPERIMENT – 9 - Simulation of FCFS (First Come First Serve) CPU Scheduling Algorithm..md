## 🎯 **AIM**

To input a list of processes with arrival time and burst time, simulate the **FCFS scheduling algorithm**, and calculate **Completion Time (CT), Waiting Time (WT), Turnaround Time (TAT)** and average values.

---

## 📚 **THEORY**

CPU scheduling decides the order in which processes are executed.

**FCFS (First Come First Serve)** is a non-preemptive scheduling algorithm where:

- The process that arrives first is executed first
- It follows a **FIFO (First In First Out)** approach

### 🔹 Key Terms:

- **Arrival Time (AT):** Time at which process arrives
- **Burst Time (BT):** Execution time required
- **Completion Time (CT):** Time when process finishes
- **Turnaround Time (TAT):**
    
```
    TAT = CT - AT
```
    
- **Waiting Time (WT):**
    
```
    WT = TAT - BT
```
    

### 🔹 Characteristics:

- Simple and easy to implement
- No starvation
- May cause **convoy effect** (long waiting time)

---

# 🧾 **ALGORITHM (FCFS)**

**Step 1:** Start

**Step 2:** Input number of processes `n`

**Step 3:** For each process, input:

- Arrival Time (AT)
- Burst Time (BT)
- Assign Process ID

---

**Step 4:** Sort processes in ascending order of Arrival Time

---

**Step 5:** Initialize:

- `time = 0`
- `totalWT = 0`, `totalTAT = 0`

---

**Step 6:** For each process:

- If CPU is idle:
    
```
    if (time < AT)  
        time = AT
```
    
- Calculate Waiting Time:
    
```
    WT = time - AT
```
    
- Update time:
    
```
    time = time + BT
```
    
- Calculate Completion Time:
    
```
    CT = time
```
    
- Calculate Turnaround Time:
    
```
    TAT = CT - AT
```
    
- Add WT and TAT to totals

---

**Step 7:** Calculate averages:

`Average WT = totalWT / n  
Average TAT = totalTAT / n`

---

**Step 8:** Display results

**Step 9:** Stop

---

# 💻 **PROGRAM**

```c
#include <stdio.h>  
  
typedef struct {  
    int pid;  
    int at;  
    int bt;  
    int ct;  
    int wt;  
    int tat;  
} Process;  
  
int main() {  
    int n;  
  
    printf("Enter number of processes: ");  
    scanf("%d", &n);  
  
    Process p[n], temp;  
  
	    printf("Enter Arrival Time and Burst Time:\n");  
    for (int i = 0; i < n; i++) {  
        p[i].pid = i + 1;  
        scanf("%d %d", &p[i].at, &p[i].bt);  
    }  
  
    // Sort by Arrival Time  
    for (int i = 0; i < n - 1; i++) {  
        for (int j = i + 1; j < n; j++) {  
            if (p[i].at > p[j].at) {  
                temp = p[i];  
                p[i] = p[j];  
                p[j] = temp;  
            }  
        }  
    }  
  
    int time = 0;  
    float totalWT = 0, totalTAT = 0;  
  
    for (int i = 0; i < n; i++) {  
  
        if (time < p[i].at)  
            time = p[i].at;  
  
        p[i].wt = time - p[i].at;  
  
        time += p[i].bt;  
        p[i].ct = time;  
  
        p[i].tat = p[i].ct - p[i].at;  
  
        totalWT += p[i].wt;  
        totalTAT += p[i].tat;  
    }  
  
    printf("\nPID\tAT\tBT\tCT\tWT\tTAT\n");  
    for (int i = 0; i < n; i++) {  
        printf("P%d\t%d\t%d\t%d\t%d\t%d\n",  
               p[i].pid, p[i].at, p[i].bt,  
               p[i].ct, p[i].wt, p[i].tat);  
    }  
  
    printf("\nAverage Waiting Time = %.2f", totalWT / n);  
    printf("\nAverage Turnaround Time = %.2f\n", totalTAT / n);  
  
    return 0;  
}
```
---

## 📤 **OUTPUT (Example)**

```
Enter number of processes: 3  
Enter Arrival Time and Burst Time:  
0 5  
1 3  
2 8  
  
PID  AT  BT  CT  WT  TAT  
P1   0   5   5   0   5  
P2   1   3   8   4   7  
P3   2   8   16  6   14  
  
Average Waiting Time = 3.33  
Average Turnaround Time = 8.67
```

---

## ✅ **RESULT**

The FCFS scheduling algorithm was successfully implemented, and the waiting time and turnaround time for each process along with their averages were calculated.

---

# 🔥 **VIVA QUESTIONS**

## 🧠 Basic

1. What is FCFS?  
    👉 First Come First Serve scheduling
2. Is FCFS preemptive?  
    👉 No

---

## ⚙️ Conceptual

3. What is convoy effect?  
    👉 Long process delays others
4. Does FCFS cause starvation?  
    👉 No

---

## 🧮 Technical

5. Why sorting is required?  
    👉 To execute in arrival order
6. Why check `time < AT`?  
    👉 To handle CPU idle condition

---

## 💀 Advanced

7. Time complexity of sorting?  
    👉 O(n²)
8. Can FCFS be improved?  
    👉 Yes, using SJF/SRTF