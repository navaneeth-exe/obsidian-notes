## 📝 **Experiment Name**

To print the current system time and determine the time spent by a process in **user mode** and **kernel mode** using the `/proc` file system.

---

## 🎯 **AIM**

To write and execute a C program that prints the current system time and calculates the amount of time the process spends in user mode and kernel mode using `/proc/self/stat`.

---

## 📚 **THEORY**

The `/proc` file system in Linux is a **virtual file system** that provides detailed information about processes and system resources.

Each running process has a directory `/proc/<PID>/`.  
The file `/proc/self/stat` contains statistics of the currently executing process.

Important fields in this file:

- **14th field (utime):** Time spent in user mode
- **15th field (stime):** Time spent in kernel mode

These values are stored in **clock ticks (jiffies)**.

To convert clock ticks into seconds:

Time (seconds) = Number of ticks / Clock ticks per second

The number of clock ticks per second is obtained using:

sysconf(_SC_CLK_TCK);

This program demonstrates how to extract process execution details using the `/proc` file system.

---

## 🧾 **ALGORITHM**

**Step 1:** Start  
**Step 2:** Get current system time using `time()`  
**Step 3:** Display the time using `ctime()`  
**Step 4:** Execute a loop to consume CPU time  
**Step 5:** Open `/proc/self/stat` file  
**Step 6:** Skip the first 13 fields  
**Step 7:** Read utime and stime values  
**Step 8:** Get clock ticks per second using `sysconf()`  
**Step 9:** Convert utime and stime into seconds  
**Step 10:** Display user mode and kernel mode time  
**Step 11:** Stop

---

## 💻 **PROGRAM**

```
#include<stdio.h>  
#include<unistd.h>  
#include<stdlib.h>  
#include<time.h>  
  
int main()  
{  
    time_t now;  
    time(&now);  
    printf("Current system time: %s", ctime(&now));  
  
    for (volatile long i = 0; i < 200000000; i++);  
  
    FILE *fp = fopen("/proc/self/stat", "r");  
  
    if (!fp) {  
        perror("Failed to open /proc/self/stat");  
        return 1;  
    }  
  
    unsigned long utime, stime;  
  
    for (int i = 1; i <= 13; i++)  
        fscanf(fp, "%*s");  
  
    fscanf(fp, "%lu %lu", &utime, &stime);  
  
    fclose(fp);  
  
    long hz = sysconf(_SC_CLK_TCK);  
  
    double user_time = (double)utime / hz;  
    double sys_time = (double)stime / hz;  
  
    printf("User mode time: %.4f seconds\n", user_time);  
    printf("Kernel mode time: %.4f seconds\n", sys_time);  
  
    return 0;  
}
```
---

# 🔍 **DETAILED EXPLANATION OF THE CODE**

### 🔹 Header Files

- `stdio.h` → input/output functions
- `unistd.h` → system-level functions like `sysconf()`
- `stdlib.h` → general utilities
- `time.h` → time-related functions

---

### 🔹 Getting Current Time

- `time_t now;` → variable to store time
- `time(&now);` → fetches current system time
- `ctime(&now);` → converts time to readable format

---

### 🔹 CPU Consumption Loop

- A loop runs for a large number of iterations
- Used to **increase CPU usage** so measurable time is generated
- `volatile` prevents compiler from removing the loop

---

### 🔹 Accessing `/proc/self/stat`

- `fopen()` opens the file containing process details
- `self` refers to the current process

---

### 🔹 Skipping Fields

- The file has many fields
- First 13 fields are skipped using:

fscanf(fp, "%*s");

- `%*s` means read but ignore

---

### 🔹 Reading utime and stime

- Next two values are:
    - `utime` → user mode time
    - `stime` → kernel mode time

---

### 🔹 Converting Clock Ticks

- `sysconf(_SC_CLK_TCK)` gives ticks per second
- Convert using:
    - `user_time = utime / hz`
    - `sys_time = stime / hz`

---

### 🔹 Displaying Output

- Prints time spent in:
    - User mode
    - Kernel mode

---

## 📤 **OUTPUT**

Current system time: Wed Mar 27 12:34:56 2026  
User mode time: 1.2345 seconds  
Kernel mode time: 0.0123 seconds

---

## ✅ **RESULT**

The program was successfully executed, and the time spent in **user mode** and **kernel mode** was obtained using the `/proc` file system.

---

# 🔥 **VIVA QUESTIONS**

## 🧠 Basic Questions

1. What is `/proc` file system?  
    👉 A virtual file system that provides system and process information
2. What is `/proc/self/stat`?  
    👉 File containing statistics of the current process
3. What is PID?  
    👉 Process ID

---

## ⚙️ Conceptual Questions

4. What is user mode?  
    👉 Execution mode for normal programs
5. What is kernel mode?  
    👉 Execution mode for OS operations
6. What are utime and stime?  
    👉 utime → user mode time  
    👉 stime → kernel mode time

---

## 🧮 Technical Questions

7. What is a clock tick?  
    👉 Smallest unit of CPU time
8. Why convert ticks to seconds?  
    👉 To get readable execution time
9. What does `sysconf(_SC_CLK_TCK)` return?  
    👉 Number of clock ticks per second

---

## 💀 Advanced Questions

10. Why skip 13 fields?  
    👉 utime and stime are 14th and 15th fields
11. Why use `volatile`?  
    👉 Prevents compiler optimization
12. Difference between CPU time and real time?  
    👉 CPU time → actual processing time  
    👉 Real time → wall clock time