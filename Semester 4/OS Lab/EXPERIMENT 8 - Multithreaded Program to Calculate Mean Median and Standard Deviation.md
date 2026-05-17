# 🎯 AIM

Write a multithreaded program that calculates the **mean, median, and standard deviation** of a list of integers using command-line arguments and three worker threads.

---

# 🧠 THEORY (COMPLETE + MERGED)

---

### 🔹 What is a Thread?

- A **thread** is the smallest unit of execution inside a process
    
- Multiple threads can run **concurrently** within the same process
    

👉 Threads share:

- Same memory
    
- Same global variables
    

---

### 🔹 What is Multithreading?

- Execution of multiple threads simultaneously
    
- Improves performance
    
- Allows parallel execution
    
- Efficient CPU utilization
    

---

### 🔹 What is pthread?

- POSIX thread library in C
    
- Used for creating and managing threads
    

---

### 🔹 Thread Functions Used

|Function|Purpose|
|---|---|
|`pthread_create()`|Creates a thread|
|`pthread_join()`|Waits for thread completion|
|`pthread_exit()`|Terminates thread|

---

### 🔹 Concept Used in This Program (IMPORTANT)

- Three threads are created:
    
    - Thread 1 → Mean
        
    - Thread 2 → Median
        
    - Thread 3 → Standard Deviation
        
- Values are stored in **global variables**:
    
    - `mean`
        
    - `median`
        
    - `stddev`
        
- Input is taken using **command-line arguments** (as per AIM)
    

---

### 🔹 Statistical Concepts

#### ✅ Mean

$$
Mean=∑xin\text{Mean} = \frac{\sum x_i}{n}​​
$$

---

#### ✅ Median

- Middle value after sorting
    
- If odd → middle element
    
- If even → average of two middle elements
    

---

#### ✅ Standard Deviation

$$
σ=∑(xi−μ)2n\sigma = \sqrt{\frac{\sum (x_i - \mu)^2}{n}}​​
$$

---

### 🔹 Important Concept from PDF (VERY IMPORTANT)

👉 From page 4 of your PDF:

- Mean thread is executed **first and joined before stddev**
    

✔ This avoids incorrect calculation

---

### 🔹 Synchronization Concept

- Standard deviation depends on mean
    
- So we must ensure:
    

Mean → calculated first → then Std Dev

👉 Done using:

pthread_join(tid1, NULL);

---

# ⚙️ ALGORITHM

🧾 ALGORITHM – EXPERIMENT 8

**Step 1:** Start

**Step 2:** Read integers from command-line arguments and store in array

**Step 3:** Declare global variables: `mean`, `median`, `stddev`, *numbers, n

**Step 4:** Create three threads using `pthread_create()`

- Thread 1 → Mean
- Thread 2 → Median
- Thread 3 → Standard Deviation

**Step 5:** In mean thread

- Calculate sum of elements
- Compute mean = sum / n

**Step 6:** In median thread

- Sort the array
- If n is odd → median = middle element
- If n is even → median = average of two middle elements

**Step 7:** In standard deviation thread

- Compute using formula:  
    stddev = √(Σ(xi − mean)² / n)

**Step 8:** Use `pthread_join()` to wait for all threads

**Step 9:** Print mean, median, and standard deviation

**Step 10:** Stop

---

# ⚙️ CODE (PDF BASED FINAL)

```c
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <math.h>

int *numbers;   // dynamic array
int n;

double mean;
double median;
double stddev;

// Mean
void* calculate_mean(void* arg)
{
    int sum = 0;

    for(int i = 0; i < n; i++)
        sum += numbers[i];

    mean = (double)sum / n;

    pthread_exit(0);
}

// Median
void* calculate_median(void* arg)
{
    int *temp = (int *)malloc(n * sizeof(int));

    // copy array
    for(int i = 0; i < n; i++)
        temp[i] = numbers[i];

    // sort (bubble-ish)
    for(int i = 0; i < n - 1; i++)
    {
        for(int j = i + 1; j < n; j++)
        {
            if(temp[i] > temp[j])
            {
                int t = temp[i];
                temp[i] = temp[j];
                temp[j] = t;
            }
        }
    }

    if(n % 2 == 0)
        median = (temp[n/2] + temp[n/2 - 1]) / 2.0;
    else
        median = temp[n/2];

    free(temp);

    pthread_exit(0);
}

// Standard Deviation
void* calculate_stddev(void* arg)
{
    double sum = 0;

    for(int i = 0; i < n; i++)
        sum += pow(numbers[i] - mean, 2);

    stddev = sqrt(sum / n);

    pthread_exit(0);
}

int main(int argc, char *argv[])
{
    pthread_t tid1, tid2, tid3;

    if(argc < 2)
    {
        printf("Usage: %s number1 number2 ...\n", argv[0]);
        return 1;
    }

    n = argc - 1;

    // dynamic allocation (instead of MAX)
    numbers = (int *)malloc(n * sizeof(int));

    for(int i = 0; i < n; i++)
        numbers[i] = atoi(argv[i+1]);

    // Mean thread
    pthread_create(&tid1, NULL, calculate_mean, NULL);
    pthread_join(tid1, NULL);   // MUST finish before stddev

    // Median & Stddev threads
    pthread_create(&tid2, NULL, calculate_median, NULL);
    pthread_create(&tid3, NULL, calculate_stddev, NULL);

    pthread_join(tid2, NULL);
    pthread_join(tid3, NULL);

    printf("Mean = %.2f\n", mean);
    printf("Median = %.2f\n", median);
    printf("Standard Deviation = %.2f\n", stddev);

    free(numbers);

    return 0;
}
```

---

# 🔄 WORKING

1. Input taken from command line
    
2. Values stored in array
    
3. Mean thread executes first
    
4. Main waits → ensures mean is ready
    
5. Median and stddev threads run
    
6. Main waits again
    
7. Final results printed
    

---

# 📤 OUTPUT

```
./exp8 10 20 30 40 50  
  
Mean = 30.00  
Median = 30.00  
Standard Deviation = 14.14
```

---

# 🧾 RESULT

The program was successfully executed using multithreading and command-line arguments to compute mean, median, and standard deviation.

---

# ⚠️ IMPORTANT NOTE (VERY IMPORTANT FOR VIVA)

👉 Without synchronization:

- Stddev may use wrong mean
    

👉 In THIS program:  
✔ Fixed using `pthread_join()`

---

# ⚡ IMPORTANT POINTS

- Uses command-line arguments
    
- Uses global variables
    
- Uses 3 threads
    
- Uses synchronization
    
- Avoids race condition

---

# 🎤 VIVA QUESTIONS WITH ANSWERS

---

## 🔹 BASIC

### 1. What is a thread?

👉 Smallest unit of execution in a process.

---

### 2. What is multithreading?

👉 Running multiple threads concurrently.

---

### 3. What is pthread?

👉 POSIX thread library in C.

---

### 4. Why use threads?

👉 To improve performance and efficiency.

---

### 5. What is pthread_create()?

👉 Used to create a thread.

---

## 🔹 INTERMEDIATE

### 6. What is pthread_join()?

👉 Waits for thread to finish.

---

### 7. What are global variables?

👉 Variables shared among threads.

---

### 8. Why is sorting needed for median?

👉 To find correct middle value.

---

### 9. What is qsort()?

👉 Built-in sorting function.

---

### 10. What is standard deviation?

👉 Measure of data spread.

---

## 🔹 ADVANCED

### 11. What is race condition?

👉 When multiple threads access shared data simultaneously.

---

### 12. Is this program free from race condition?

👉 No (stddev depends on mean).

---

### 13. How to fix it?

👉 Use synchronization (mutex or condition variable).

---

### 14. Difference between process and thread?

|Process|Thread|
|---|---|
|separate memory|shared memory|
|heavy|lightweight|

---

### 15. What is synchronization?

👉 Controlling execution order.

---

### 16. What is mutex?

👉 Lock mechanism for threads.

---

### 17. What happens without pthread_join()?

👉 Main may exit before threads finish.

---

### 18. What is concurrency?

👉 Multiple tasks executing simultaneously.

---

### 19. What is parallelism?

👉 Tasks running at the same time on multiple CPUs.

---

### 20. What is thread safety?

👉 Safe access to shared data.

---

# 🧠 ONE-LINE SUMMARY

👉 Multiple threads are used to compute mean, median, and standard deviation concurrently using shared data.