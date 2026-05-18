ALGORITHM – FCFS Scheduling

Step 1:

Start


---

Step 2:

Input:

Number of processes

Arrival Time (AT)

Burst Time (BT)


Assign Process ID.


---

Step 3:

Sort processes according to Arrival Time using simple sorting.

If two processes have same Arrival Time:

Select process with smaller Process ID.



---

Step 4:

Initialize:

time = 0
totalWT = 0
totalTAT = 0


---

Step 5:

Repeat for each process in sorted order:

If current time is less than Arrival Time:

time = AT

Execute process completely.


---

Step 6:

Calculate:

Completion Time:

CT = time + BT

Update current time:

time = CT

Turnaround Time:

TAT = CT - AT

Waiting Time:

WT = TAT - BT

Add to totals:

totalWT += WT
totalTAT += TAT


---

Step 7:

After all processes complete:

Calculate:

Average Waiting Time:

AvgWT = totalWT / n

Average Turnaround Time:

AvgTAT = totalTAT / n


---

Step 8:

Display:

Process ID

Arrival Time

Burst Time

Completion Time

Turnaround Time

Waiting Time

Average WT

Average TAT



---

Step 9:

Stop


---

FCFS Scheduling Program in C

#include <stdio.h>

typedef struct {

    int pid;
    int at;
    int bt;

    int ct;
    int tat;
    int wt;

} Process;

int main() {

    int n;

    printf("Enter number of processes: ");
    scanf("%d", &n);

    Process p[n];

    // Input
    printf("Enter Arrival Time and Burst Time:\n");

    for(int i = 0; i < n; i++) {

        p[i].pid = i + 1;

        printf("P%d:\n", p[i].pid);

        printf("AT: ");
        scanf("%d", &p[i].at);

        printf("BT: ");
        scanf("%d", &p[i].bt);
    }

    // Simple Sorting using nested loop
    for(int i = 0; i < n; i++) {

        for(int j = i + 1; j < n; j++) {

            if(p[i].at > p[j].at) {

                Process temp = p[i];
                p[i] = p[j];
                p[j] = temp;
            }
        }
    }

    int time = 0;
    float totalWT = 0, totalTAT = 0;

    // FCFS Scheduling
    for(int i = 0; i < n; i++) {

        if(time < p[i].at) {

            time = p[i].at;
        }

        p[i].ct = time + p[i].bt;

        time = p[i].ct;

        p[i].tat = p[i].ct - p[i].at;

        p[i].wt = p[i].tat - p[i].bt;

        totalWT += p[i].wt;
        totalTAT += p[i].tat;
    }

    // Output
    printf("\nPID\tAT\tBT\tCT\tTAT\tWT\n");

    for(int i = 0; i < n; i++) {

        printf("P%d\t%d\t%d\t%d\t%d\t%d\n",

               p[i].pid,
               p[i].at,
               p[i].bt,
               p[i].ct,
               p[i].tat,
               p[i].wt
        );
    }

    printf("\nAverage Waiting Time = %.2f", totalWT / n);

    printf("\nAverage Turnaround Time = %.2f\n", totalTAT / n);

    return 0;
}