# 🎯 **AIM**

To simulate the **C-SCAN disk scheduling algorithm** for a disk containing 5000 cylinders numbered from 0 to 4999 and calculate the total head movement.

The program generates:

- Random disk requests
- Initial head position using command line argument

and computes the total seek movement.

---

# 📚 **THEORY**

C-SCAN (Circular SCAN) is a disk scheduling algorithm used in operating systems.

It moves the disk head in only one direction.

---

## 🔹 Working Principle

- Head services requests while moving toward higher cylinders
- After reaching the last cylinder:
    - Head jumps back to cylinder 0
    - Continues servicing remaining requests

---

## 🔹 Advantages

- Uniform waiting time
- Better fairness compared to SCAN

---

# 🧾 **ALGORITHM – C-SCAN**

### Step 1:

Start

---

### Step 2:

Read initial head position using command line argument.

---

### Step 3:

Generate random disk requests between:

```
0 to 4999
```

---

### Step 4:

Sort all disk requests in ascending order.

---

### Step 5:

Initialize:

- `current = head`
- `total = 0`

---

### Step 6:

Service all requests greater than or equal to head position:

- Calculate head movement
- Update current head position

---

### Step 7:

Move head to last cylinder:

```
4999
```

---

### Step 8:

Jump from last cylinder to first cylinder:

```
0
```

---

### Step 9:

Service remaining requests smaller than initial head position.

---

### Step 10:

Display total head movement.

---

### Step 11:

Stop

---

# 💻 **PROGRAM**

```c title=cscan.c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define CYLINDERS 5000
#define REQUESTS 10

void sort(int arr[], int n) {

    for(int i = 0; i < n - 1; i++) {

        for(int j = i + 1; j < n; j++) {

            if(arr[i] > arr[j]) {

                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
    }
}

int main(int argc, char *argv[]) {

    if(argc != 2) {

        printf("Usage: %s <initial_head_position>\n", argv[0]);
        return 1;
    }

    int head = atoi(argv[1]);

    int req[REQUESTS];

    srand(time(0));

    // Generate random requests
    printf("Disk Requests:\n");

    for(int i = 0; i < REQUESTS; i++) {

        req[i] = rand() % CYLINDERS;

        printf("%d ", req[i]);
    }

    printf("\n");

    sort(req, REQUESTS);

    int total = 0;
    int current = head;

    printf("\nSeek Sequence:\n");

    // Service requests greater than head
    for(int i = 0; i < REQUESTS; i++) {

        if(req[i] >= head) {

            printf("%d ", req[i]);

            total += abs(current - req[i]);

            current = req[i];
        }
    }

    // Move to end of disk
    total += abs(current - (CYLINDERS - 1));

    current = CYLINDERS - 1;

    // Jump to beginning
    total += abs(current - 0);

    current = 0;

    // Service remaining requests
    for(int i = 0; i < REQUESTS; i++) {

        if(req[i] < head) {

            printf("%d ", req[i]);

            total += abs(current - req[i]);

            current = req[i];
        }
    }

    printf("\n\nTotal Head Movement = %d\n", total);

    return 0;
}
```

---

# 📤 **COMPILATION & EXECUTION**

```
gcc cscan.c -o cscan./cscan 2000
```

---

# 📤 **SAMPLE OUTPUT**

```
Disk Requests:345 1200 4567 890 3200 499 2500 4100 1500 3800Seek Sequence:2500 3200 3800 4100 4567 345 499 890 1200 1500Total Head Movement = 8465
```

---

# 🔍 **DETAILED CODE EXPLANATION**

---

## 🔹 Header Files

```
#include <stdio.h>#include <stdlib.h>#include <time.h>
```

### Used for:

- `printf()`
- `atoi()`
- `rand()`
- `time()`

---

## 🔹 Constants

```
#define CYLINDERS 5000#define REQUESTS 10
```

👉 Disk has:

```
0 → 4999 cylinders
```

👉 Generates 10 requests.

---

## 🔹 `sort()` Function

```
sort(req, REQUESTS);
```

👉 Sorts requests in ascending order.

---

## 🔹 Command Line Argument

```
int head = atoi(argv[1]);
```

👉 Reads initial head position.

---

## 🔹 Generate Random Requests

```
req[i] = rand() % CYLINDERS;
```

👉 Generates requests between:

```
0 → 4999
```

---

## 🔹 Service Higher Requests

```
if(req[i] >= head)
```

👉 Services all requests ahead of head.

---

## 🔹 Head Movement

```
total += abs(current - req[i]);
```

👉 Calculates seek distance.

---

## 🔹 Move to End

```
total += abs(current - (CYLINDERS - 1));
```

👉 Head reaches cylinder 4999.

---

## 🔹 Circular Jump

```
total += abs(current - 0);
```

👉 Jump from 4999 → 0.

---

## 🔹 Service Remaining Requests

```
if(req[i] < head)
```

👉 Services lower requests after jump.

---

# ✅ **RESULT**

The C-SCAN disk scheduling algorithm was successfully implemented and the total head movement was calculated.

---

# 🔥 **VIVA QUESTIONS**

---

## ❓ What is C-SCAN?

👉 Circular SCAN disk scheduling algorithm.

---

## ❓ How does C-SCAN work?

👉 Head moves in one direction and jumps back to beginning after reaching end.

---

## ❓ Why sort requests?

👉 To service requests sequentially.

---

## ❓ Why use `abs()`?

👉 To calculate seek distance.

---

## ❓ What is seek time?

👉 Time required to move disk head.

---

## ❓ Difference between SCAN and C-SCAN?

👉 SCAN moves both directions; C-SCAN moves only one direction.

---

## ❓ Why jump back to 0?

👉 Circular servicing mechanism.

---

## ❓ Advantage of C-SCAN?

👉 Uniform waiting time and fairness.