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

# **FULL CODE EXPLANATION – SSTF**

---

## 🔹 **HEADER FILES**

```
#include <stdio.h>  
#include <stdlib.h>  
#include <math.h>  
#include <time.h>
```

- `stdio.h` → input/output (`printf`, `scanf`)
- `stdlib.h` → `rand()`, `abs()`
- `math.h` → math functions (not heavily used here)
- `time.h` → for random seed (`time(NULL)`)

---

## 🔹 **MACROS**

```
#define MAX_CYLINDER 4999  
#define REQUESTS 10
```

- Disk size → cylinders from **0 to 4999**
- Number of disk requests → **10**

---

# ⚙️ **SSTF FUNCTION (CORE LOGIC)**

```
int sstf(int head, int req[], int n)
```

### Parameters:

- `head` → initial head position
- `req[]` → array of requests
- `n` → number of requests

---

## 🔹 **VARIABLES**

```
int visited[REQUESTS] = {0};  
int total = 0, count = 0;  
int cur = head;
```

- `visited[]` → tracks which requests are completed
- `total` → total head movement
- `count` → number of completed requests
- `cur` → current head position

---

## 🔁 **MAIN LOOP**

```
while (count < n)
```

👉 Loop runs until all requests are served

---

## 🔍 **FIND NEAREST REQUEST**

```
int min = 999999, idx = -1;
```

- `min` → stores smallest distance
- `idx` → index of closest request

---

### 🔹 Loop through all requests:

```
for (int i = 0; i < n; i++)
```

---

### 🔹 Check unvisited requests:

```
if (!visited[i])
```
👉 Only consider pending requests

---

### 🔹 Calculate distance:

```
int d = abs_diff(cur, req[i]);
```

---

### 🔹 Find minimum:

```
if (d < min) {  
    min = d;  
    idx = i;  
}
```

👉 Choose closest request → **SSTF logic**

---

## 🔄 **UPDATE VALUES**

```
visited[idx] = 1;  
total += abs_diff(cur, req[idx]);  
cur = req[idx];  
count++;
```

### What happens:

1. Mark request as done
2. Add movement to total
3. Move head
4. Increase count

---

## 🔚 **RETURN TOTAL MOVEMENT**

```
return total;
```

---

# 🧾 **MAIN FUNCTION**

---

## 🔹 RANDOM SEED

```
srand(time(NULL));
```

👉 Ensures different random numbers every run

---

## 🔹 INPUT HEAD POSITION

```
scanf("%d", &head);
```

---

## 🔹 ARRAY DECLARATION

```
int requests[REQUESTS];
```

---

## 🔹 GENERATE RANDOM REQUESTS

```
requests[i] = rand() % (MAX_CYLINDER + 1);
```

👉 Generates values between **0 and 4999**

---

## 🔹 PRINT REQUESTS
```
printf("%d ", requests[i]);
```

---

## 🔹 CALL SSTF FUNCTION

```
int total = sstf(head, requests, REQUESTS);
```

👉 Calculates total head movement

---

## 🔹 OUTPUT

```
printf("Total head movement (SSTF): %d\n", total);
```

---

# 🔥 **HOW THE ALGORITHM WORKS (SIMPLE FLOW)**

```
Example:

Head = 100  
Requests = [120, 80, 200]
```

### Steps:

1. From 100 → nearest is 80 (distance 20)
2. From 80 → nearest is 120 (distance 40)
3. From 120 → nearest is 200 (distance 80)

👉 Total = 20 + 40 + 80 = **140**
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