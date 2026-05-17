# 🎯 **AIM**

To input a list of processes with Arrival Time, Burst Time, and Priority, and simulate the **Non-Preemptive Priority Scheduling Algorithm** to calculate:

- Completion Time (CT)
- Waiting Time (WT)
- Turnaround Time (TAT)
- Average Waiting Time
- Average Turnaround Time

---

# 📚 **THEORY**

Priority Scheduling is a CPU scheduling algorithm in which each process is assigned a priority.

- The process with highest priority gets CPU first.
- In this program:

```
Higher number = Higher priority
```

---

## 🔹 Non-Preemptive Priority Scheduling

In non-preemptive scheduling:

- Once a process starts execution,
- It continues until completion.
- CPU cannot be taken away from the running process.

---

# 🔹 Important Terms

### Arrival Time (AT)

Time at which process enters ready queue.

---

### Burst Time (BT)

CPU execution time required by process.

---

### Priority (PR)

Value used to decide execution order.

---

### Completion Time (CT)

Time at which process finishes execution.

---

### Turnaround Time (TAT)

```
TAT = CT - AT
```

---

### Waiting Time (WT)

```
WT = TAT - BT
```

---

# 🧾 **ALGORITHM – Non-Preemptive Priority Scheduling**

### Step 1:

Start

### Step 2:

Input:

- Number of processes
- Arrival Time (AT)
- Burst Time (BT)
- Priority (PR)

Assign Process ID and initialize:

```
completed = 0
```

### Step 3:

Initialize:

```
time = 0
completed = 0
totalWT = 0
totalTAT = 0
```

### Step 4:

Repeat until all processes are completed:

- Find process such that:
    - Arrival Time ≤ current time
    - Process is not completed
    - Process has highest priority
- If two processes have same priority:
    - Select process with smaller arrival time

### Step 5:

If no process is available:

```
time++
```

### Step 6:

Else:

Execute selected process completely.

Calculate:

```
CT = time + BT
```

Update current time:

```
time = CT
```

Calculate:

```
TAT = CT - AT
```

```
WT = TAT - BT
```

Add WT and TAT to totals.

Mark process as completed.

Increment completed count.


### Step 7:

Repeat Steps 4–6 until all processes finish execution.


### Step 8:

Calculate averages:

```
Average WT = totalWT / n
```

```
Average TAT = totalTAT / n
```

### Step 9:

Display:

- PID
- AT
- BT
- Priority
- CT
- WT
- TAT

### Step 10:

Stop

---

# 💻 **PROGRAM**

```c title=nonPremtive.c
#include <stdio.h>

typedef struct {

    int pid;
    int at;
    int bt;
    int pr;

    int ct;
    int tat;
    int wt;

    int completed;

} Process;

int main() {

    int n;

    printf("Enter number of processes: ");
    scanf("%d", &n);

    Process p[n];

    // Input
    printf("Enter Arrival Time, Burst Time and Priority:\n");

    for(int i = 0; i < n; i++) {

        p[i].pid = i + 1;

        printf("P%d: ", p[i].pid);

        scanf("%d %d %d",
              &p[i].at,
              &p[i].bt,
              &p[i].pr);

        p[i].completed = 0;
    }

    int time = 0;
    int completed = 0;

    float totalWT = 0;
    float totalTAT = 0;

    while(completed < n) {

        int idx = -1;
        int highest = -9999;

        // Find highest priority process
        for(int i = 0; i < n; i++) {

            if(p[i].at <= time &&
               p[i].completed == 0) {

                if(p[i].pr > highest) {

                    highest = p[i].pr;
                    idx = i;
                }

                // Tie breaking using arrival time
                else if(p[i].pr == highest) {

                    if(p[i].at < p[idx].at) {
                        idx = i;
                    }
                }
            }
        }

        // CPU Idle
        if(idx == -1) {

            time++;
        }

        else {

            // Execute process completely
            time += p[idx].bt;

            p[idx].ct = time;

            p[idx].tat =
                p[idx].ct - p[idx].at;

            p[idx].wt =
                p[idx].tat - p[idx].bt;

            totalWT += p[idx].wt;
            totalTAT += p[idx].tat;

            p[idx].completed = 1;

            completed++;
        }
    }

    // Output
    printf("\nPID\tAT\tBT\tPR\tCT\tTAT\tWT\n");

    for(int i = 0; i < n; i++) {

        printf("P%d\t%d\t%d\t%d\t%d\t%d\t%d\n",

               p[i].pid,
               p[i].at,
               p[i].bt,
               p[i].pr,
               p[i].ct,
               p[i].tat,
               p[i].wt);
    }

    printf("\nAverage Waiting Time = %.2f",
           totalWT / n);

    printf("\nAverage Turnaround Time = %.2f\n",
           totalTAT / n);

    return 0;
}
```


---

# 📤 **OUTPUT (Example)**

```
Enter number of processes: 4

Enter Arrival Time, Burst Time and Priority:
P1: 0 4 2
P2: 1 3 4
P3: 2 5 1
P4: 3 2 3

PID    AT   BT   PR   CT   TAT   WT
P1     0    4    2    4    4     0
P2     1    3    4    7    6     3
P3     2    5    1    14   12    7
P4     3    2    3    9    6     4

Average Waiting Time = 3.50
Average Turnaround Time = 7.00
```

---

# 🔍 **DETAILED CODE EXPLANATION**

---

## 🔹 Structure

```
typedef struct
```

👉 Stores process information:

- PID
- AT
- BT
- Priority
- CT
- TAT
- WT

---

## 🔹 `completed`

```
int completed;
```

👉 Tracks whether process has finished execution.

---

## 🔹 Find Highest Priority Process

```
if(p[i].pr > highest)
```

👉 Selects process with highest priority.

---

## 🔹 Tie Breaking

```
if(p[i].at < p[idx].at)
```

👉 If priorities are same,  
choose earlier arriving process.

---

## 🔹 CPU Idle

```
if(idx == -1)
```

👉 No process available at current time.

---

## 🔹 Execute Process

```
time += p[idx].bt;
```

👉 Non-preemptive:  
Process executes completely.

---

## 🔹 Completion Time

```
p[idx].ct = time;
```

---

## 🔹 Turnaround Time

```
TAT = CT - AT
```

---

## 🔹 Waiting Time

```
WT = TAT - BT
```

---

# ✅ **RESULT**

The Non-Preemptive Priority Scheduling Algorithm was successfully implemented and the average waiting time and turnaround time were calculated.

---

# 🔥 **VIVA QUESTIONS**

---

## ❓ What is Priority Scheduling?

👉 CPU scheduling based on priority.

---

## ❓ What is Non-Preemptive scheduling?

👉 Once process starts execution, it runs until completion.

---

## ❓ Which process executes first?

👉 Process with highest priority.

---

## ❓ What if two processes have same priority?

👉 Tie is broken using arrival time.

---

## ❓ What is starvation?

👉 Low-priority process may wait indefinitely.

---

## ❓ Advantage of Priority Scheduling?

👉 Important processes execute first.

---

## ❓ Disadvantage?

👉 Starvation may occur.

---

## ❓ Difference between Preemptive and Non-Preemptive?

👉 Preemptive can interrupt running process; Non-preemptive cannot.