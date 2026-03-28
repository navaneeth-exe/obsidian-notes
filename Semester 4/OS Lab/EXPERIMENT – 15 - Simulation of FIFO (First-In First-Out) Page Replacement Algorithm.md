## 🎯 **AIM**

To generate a random page reference string and simulate the **FIFO page replacement algorithm** to determine the number of page faults.

---

## 📚 **THEORY**

FIFO (First-In First-Out) is a page replacement algorithm where:

- The page that **enters memory first is replaced first**
- It follows a **queue-based approach**

### 🔹 Key Idea:

> Oldest page in memory is removed when a new page needs to be loaded.

---

### 🔹 Concepts:

- **Page** → unit of memory
- **Frame** → slot in memory
- **Page Fault** → occurs when page is not in memory

---

# 🧾 **CORRECT ALGORITHM (MATCHES YOUR CODE)**

---

### 🔹 **Step 1:** Start

### 🔹 **Step 2:** Read command-line arguments:

- Length of reference string `n`
- Number of frames

---

### 🔹 **Step 3:** Generate random page reference string

- Values between **0 to 9**

---

### 🔹 **Step 4:** Initialize:

- Frame array with `-1` (empty)
- `pageFaults = 0`
- Pointer `k = 0` (FIFO index)

---

### 🔹 **Step 5:** For each page in reference string:

- Check if page is already present in frames
    - If yes → do nothing
- If not present:
    - Replace page at position `k`
    - Update:
        
```
        k = (k + 1) % frames
```
        
    - Increment page faults

---

### 🔹 **Step 6:** Display total page faults

### 🔹 **Step 7:** Stop

---

# 💻 **PROGRAM (CLEAN VERSION)**

```
#include <stdio.h>  
#include <stdlib.h>  
#include <time.h>  
  
#define MAX_PAGES 100  
  
// FIFO Page Replacement  
int fifo(int pages[], int n, int frames) {  
    int fr[10], pageFaults = 0, k = 0;  
  
    // Initialize frames  
    for (int i = 0; i < frames; i++)  
        fr[i] = -1;  
  
    for (int i = 0; i < n; i++) {  
        int found = 0;  
  
        // Check if page is already present  
        for (int j = 0; j < frames; j++) {  
            if (fr[j] == pages[i]) {  
                found = 1;  
                break;  
            }  
        }  
  
        // Page fault  
        if (!found) {  
            fr[k] = pages[i];  
            k = (k + 1) % frames; // circular queue  
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
  
    int faults = fifo(pages, n, frames);  
  
    printf("\nTotal page faults (FIFO): %d\n", faults);  
  
    return 0;  
}
```

---

## 📤 **OUTPUT (Example)**

Generated page reference string:  
1 2 3 4 1 2 5 1 2 3  
  
Total page faults (FIFO): 8


---

# **DETAILED CODE EXPLANATION – FIFO PAGE REPLACEMENT**

---

# 🔹 **HEADER FILES**

```
#include <stdio.h>  
#include <stdlib.h>  
#include <time.h>
```

### Why:

- `stdio.h` → `printf`
- `stdlib.h` → `atoi()`, `rand()`
- `time.h` → `time(NULL)` for random numbers

---

# 🔹 **MACRO**

```
#define MAX_PAGES 100
```

👉 Maximum size of reference string = 100

---

# ⚙️ **FIFO FUNCTION (CORE LOGIC)**

```
int fifo(int pages[], int n, int frames)
```

### Parameters:

- `pages[]` → page reference string
- `n` → number of pages
- `frames` → number of memory frames

---

## 🔹 **VARIABLES**

```
int fr[10], pageFaults = 0, k = 0;
```

- `fr[]` → memory frames
- `pageFaults` → count of faults
- `k` → pointer (FIFO index)

---

## 🔹 **INITIALIZE FRAMES**

`for (int i = 0; i < frames; i++)  
    fr[i] = -1;`

👉 `-1` means empty frame

---

# 🔁 **MAIN LOOP**

```
for (int i = 0; i < n; i++)
```

👉 Loop through each page request

---

## 🔍 **CHECK IF PAGE EXISTS**
```
int found = 0;  
  
for (int j = 0; j < frames; j++) {  
    if (fr[j] == pages[i]) {  
        found = 1;  
        break;  
    }  
}
```

👉 Search all frames  
👉 If found → no page fault

---

# ❌ **PAGE FAULT CONDITION**

```
if (!found)
```
👉 Page not in memory

---

## 🔄 **REPLACE PAGE (FIFO LOGIC)**

```
fr[k] = pages[i];
```

👉 Replace the **oldest page**

---

## 🔁 **UPDATE POINTER**

```
k = (k + 1) % frames;
```

👉 Circular movement

### Example:

`frames = 3  `
  
k = 0 → 1 → 2 → 0 → 1 → ...

👉 Works like a **queue**

---

## 🔺 **INCREMENT FAULT**

```
pageFaults++;
```

---

# 🔚 **RETURN RESULT**

```
return pageFaults;
```
---

# 🚀 **MAIN FUNCTION**

---

## 🔹 **COMMAND LINE CHECK**

```
if (argc != 3)
```

👉 Expect:

```
./program 10 3
```

---

## 🔹 **READ INPUT**

```
int n = atoi(argv[1]);  
int frames = atoi(argv[2]);
```

👉 Convert string → integer

---

## 🔹 **VALIDATION**

```
if (n <= 0 || n > MAX_PAGES || frames < 1 || frames > 7)
```

👉 Ensures valid input

---

# 🔹 **RANDOM PAGE GENERATION**

```
pages[i] = rand() % 10;
```
👉 Generates numbers from 0–9

---

## 🔹 **DISPLAY PAGES**

```
printf("%d ", pages[i]);
```

---

# 🔹 **CALL FIFO FUNCTION**

```
int faults = fifo(pages, n, frames);
```

👉 Executes algorithm

---

# 🔹 **OUTPUT**

```
printf("Total page faults: %d\n", faults);
```

---

# 🧠 **HOW FIFO WORKS (FLOW)**

Example:

```
Frames = 3  
Pages = 1 2 3 4
```

### Steps:

```
1. 1 → fault → [1 _ _]
2. 2 → fault → [1 2 _]
3. 3 → fault → [1 2 3]
4. 4 → replace 1 → [4 2 3]
```

👉 Oldest removed first
---

## ✅ **RESULT**

The FIFO page replacement algorithm was successfully implemented and the number of page faults was calculated.

---

# 🔥 **VIVA QUESTIONS**

## 🧠 Basic

1. What is FIFO?  
    👉 First-In First-Out page replacement
2. What is page fault?  
    👉 Page not found in memory

---

## ⚙️ Conceptual

3. Why use FIFO?  
    👉 Simple implementation
4. Disadvantage?  
    👉 May cause more faults (Belady’s anomaly)

---

## 🧮 Technical

5. What is `k` variable?  
    👉 Points to next frame to replace
6. Why `% frames`?  
    👉 Circular queue behavior

---

## 💀 Advanced

7. What is Belady’s anomaly?  
    👉 More frames → more faults (FIFO issue)

---

## 🧠 PRO LINE 😎

> “FIFO replaces the oldest page using a circular pointer, simulating queue behavior in memory frames.”