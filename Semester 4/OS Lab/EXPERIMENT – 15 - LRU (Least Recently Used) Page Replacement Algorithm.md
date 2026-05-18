# 🎯 **AIM**

To generate a random page reference string and simulate the **LRU page replacement algorithm** to determine the number of page faults incurred.

---

# 📚 **THEORY**

LRU (Least Recently Used) is a page replacement algorithm used in operating systems.

It replaces:lll

> The page that has not been usesd for the longest period of time.

---

## 🔹 Key Idea

- Frequently used pages are likely to be used again
- Recently used pages are kept in memory
- Least recently used page is replaced

---

## 🔹 Important Terms

- **Page** → unit of memory
- **Frame** → memory slot
- **Page Fault** → occurs when page is not present in memory

---

# 🧾 **ALGORITHM**

### Step 1:

Start

### Step 2:

Read command-line arguments:

- Length of reference string
- Number of frames

### Step 3:

Generate random page reference string (0–9)

### Step 4:

Initialize:

- Frame array with `-1`
- Time array to track recent usage
- `pageFaults = 0`
- `counter = 0`

### Step 5:

For each page in reference string:

- Check if page already exists in frames
    - If found:
        - Update usage time
- Else:
    - Find least recently used page
    - Replace it
    - Increment page faults

### Step 6:

Display total page faults

### Step 7:

Stop

---

# 💻 **PROGRAM**

```c title:LRU.c c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define MAX_PAGES 100

// LRU Page Replacement
int lru(int pages[], int n, int frames) {

    int fr[10], time[10];
    int pageFaults = 0, counter = 0;

    // Initialize frames
    for (int i = 0; i < frames; i++) {
        fr[i] = -1;
        time[i] = 0;
    }

    for (int i = 0; i < n; i++) {

        int found = 0;

        // Check if page exists
        for (int j = 0; j < frames; j++) {

            if (fr[j] == pages[i]) {
                counter++;
                time[j] = counter;
                found = 1;
                break;
            }
        }

        // Page Fault
        if (!found) {

            int pos = 0;

            // Find least recently used page
            for (int j = 1; j < frames; j++) {
                if (time[j] < time[pos])
                    pos = j;
            }

            // Replace page
            fr[pos] = pages[i];

            counter++;
            time[pos] = counter;

            pageFaults++;
        }
    }

    return pageFaults;
}

int main(int argc, char *argv[]) {

    if (argc != 3) {
        printf("Usage: %s <reference_string_length> <num_frames>\n", argv[0]);
        return 1;
    }

    int n = atoi(argv[1]);
    int frames = atoi(argv[2]);

    int pages[MAX_PAGES];

    if (n <= 0 || n > MAX_PAGES || frames < 1 || frames > 7) {
        printf("Invalid arguments.\n");
        return 1;
    }

    srand(time(NULL));

    printf("\nGenerated page reference string:\n");

    for (int i = 0; i < n; i++) {
        pages[i] = rand() % 10;
        printf("%d ", pages[i]);
    }

    printf("\n");

    int faults = lru(pages, n, frames);

    printf("\nTotal page faults (LRU): %d\n", faults);

    return 0;
}
```

---

# 📤 **SAMPLE OUTPUT**

```
Generated page reference string:1 2 3 2 4 1 5 2 1 6Total page faults (LRU): 7
```

---

# 🔍 **DETAILED CODE EXPLANATION**

---

## 🔹 `fr[]`

```
int fr[10];
```

👉 Stores pages currently present in memory frames.

---

## 🔹 `time[]`

```
int time[10];
```

👉 Stores recent usage time of pages.

---

## 🔹 `counter`

```
counter++;
```

👉 Works like timestamp.

Higher counter value = more recently used.

---

## 🔹 Page Hit Check

```
if (fr[j] == pages[i])
```

👉 If page already exists:

- No page fault
- Update usage time

---

## 🔹 Find Least Recently Used Page

```
if (time[j] < time[pos])
```

👉 Smallest time value = oldest unused page.

---

## 🔹 Replace Page

```
fr[pos] = pages[i];
```

👉 Replaces least recently used page.

---

# ✅ **RESULT**

The LRU page replacement algorithm was successfully implemented and the total number of page faults was determined.

---

# 🔥 **VIVA QUESTIONS**

---

## ❓ What is LRU?

👉 Least Recently Used page replacement algorithm.

---

## ❓ Which page is replaced?

👉 The page not used for longest time.

---

## ❓ Why use `time[]` array?

👉 To track recent usage of pages.

---

## ❓ Why use `counter`?

👉 To maintain usage order.

---

## ❓ Advantage of LRU?

👉 Better performance than FIFO.

---

## ❓ Does LRU suffer from Belady’s anomaly?

👉 No.

---

## ❓ Difference between FIFO and LRU?

👉 FIFO replaces oldest loaded page, LRU replaces least recently used page.