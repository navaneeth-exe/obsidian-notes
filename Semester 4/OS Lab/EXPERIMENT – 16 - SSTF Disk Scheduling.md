## 🎯 **AIM**

To implement the **Shortest Seek Time First (SSTF)** disk scheduling algorithm and calculate total head movement.

---

## 📚 **THEORY**

SSTF (Shortest Seek Time First) selects the disk request that is **closest to the current head position**.

- It reduces total seek time
- Improves performance compared to FCFS
- But may cause **starvation** for far requests

👉 Idea:

> Always move the disk head to the nearest request next.

---

# 🧾 **ALGORITHM**

**Step 1:** Start

**Step 2:** Read initial head position

**Step 3:** Generate or input disk requests

**Step 4:** Initialize:

- `visited[]` array = 0
- `total = 0`
- `current = head`

**Step 5:** Repeat until all requests are served

- Find nearest unvisited request
- Calculate distance = |current – request|
- Add distance to total
- Mark request as visited
- Move head to that request

**Step 6:** Print total head movement

**Step 7:** Stop

---
```
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <time.h>

#define MAX_CYLINDER 4999
#define REQUESTS 10

// Function to find absolute difference
int abs_diff(int a, int b) {
    return abs(a - b);
}

// SSTF algorithm
int sstf(int head, int req[], int n) {
    int visited[REQUESTS] = {0}; // track serviced requests
    int total = 0, count = 0;
    int cur = head; // current head position

    while (count < n) {
        int min = 999999, idx = -1;

        // find nearest request
        for (int i = 0; i < n; i++) {
            if (!visited[i]) {
                int d = abs_diff(cur, req[i]);
                if (d < min) {
                    min = d;
                    idx = i;
                }
            }
        }

        visited[idx] = 1; // mark visited
        total += abs_diff(cur, req[idx]); // add movement
        cur = req[idx]; // move head
        count++;
    }

    return total;
}

int main() {
    srand(time(NULL)); // random generator

    int head;
    printf("Enter initial head position (0–4999): ");
    scanf("%d", &head);

    int requests[REQUESTS];

    // generate random requests
    printf("\nGenerated requests:\n");
    for (int i = 0; i < REQUESTS; i++) {
        requests[i] = rand() % (MAX_CYLINDER + 1);
        printf("%d ", requests[i]);
    }
    printf("\n");

    int total = sstf(head, requests, REQUESTS);

    printf("\nTotal head movement (SSTF): %d\n", total);

    return 0;
}
```


---

## ✅ **RESULT**

The SSTF disk scheduling algorithm was successfully implemented, and the total head movement was calculated.

---

# 🔥 **VIVA QUESTIONS**

## 🧠 Basic

1. What is SSTF?  
    👉 Selects closest disk request
2. What is seek time?  
    👉 Time to move disk head

---

## ⚙️ Conceptual

3. Why is SSTF better than FCFS?  
    👉 Less head movement
4. Disadvantage of SSTF?  
    👉 Starvation

---

## 🧮 Technical

5. What is `visited[]` used for?  
    👉 Track completed requests
6. Why use `abs()`?  
    👉 To calculate distance

---

## 💀 Advanced

7. Can SSTF guarantee fairness?  
    👉 No
8. Time complexity?  
    👉 O(n²)