# 🎯 AIM

Write a multithreaded program that calculates the **mean, median, and standard deviation** of a list of integers using three separate threads.

---

# 🧠 THEORY (EXPLANATION)

### 🔹 What is a Thread?

- A **thread** is the smallest unit of execution inside a process
    
- Multiple threads can run **concurrently** within the same process
    

👉 Threads share:

- Same memory
    
- Same global variables
    

---

### 🔹 Why Multithreading?

- Improves performance
    
- Allows parallel execution
    
- Efficient use of CPU
    

---

### 🔹 What is pthread?

- POSIX thread library in C
    
- Used for creating and managing threads
    

---

### 🔹 Functions Used

|Function|Purpose|
|---|---|
|`pthread_create()`|Create thread|
|`pthread_join()`|Wait for thread|
|`pthread_exit()`|Terminate thread|

---

### 🔹 Statistical Concepts

#### ✅ Mean

Mean=∑xin\text{Mean} = \frac{\sum x_i}{n}Mean=n∑xi​​

---

#### ✅ Median

- Middle value after sorting
    
- Even → average of two middle values
    
- Odd → middle element
    

---

#### ✅ Standard Deviation

σ=∑(xi−μ)2n\sigma = \sqrt{\frac{\sum (x_i - \mu)^2}{n}}σ=n∑(xi​−μ)2​​

---

# ⚙️ ALGORITHM

1. Start
    
2. Read number of elements
    
3. Store elements in array
    
4. Declare global variables (mean, median, stddev)
    
5. Create 3 threads:
    
    - Thread 1 → Mean
        
    - Thread 2 → Median
        
    - Thread 3 → Standard Deviation
        
6. Wait for all threads using `pthread_join()`
    
7. Print results
    
8. End
    

---

# ⚙️ CODE (CORRECTED + CLEAN)

#include<stdio.h>  
#include<stdlib.h>  
#include<pthread.h>  
#include<math.h>  
  
double mean, median, stddev;  
int *numbers;  
int count;  
  
void *calculate_mean(void *arg);  
void *calculate_median(void *arg);  
void *calculate_stddev(void *arg);  
  
int compare_ints(const void *a, const void *b)  
{  
    return (*(int *)a - *(int *)b);  
}  
  
int main()  
{  
    printf("Enter the number of elements: ");  
    scanf("%d", &count);  
  
    if(count <= 0)  
    {  
        printf("Invalid input\n");  
        return 1;  
    }  
  
    numbers = malloc(count * sizeof(int));  
  
    printf("Enter numbers:\n");  
    for(int i = 0; i < count; i++)  
    {  
        scanf("%d", &numbers[i]);  
    }  
  
    pthread_t t1, t2, t3;  
  
    pthread_create(&t1, NULL, calculate_mean, NULL);  
    pthread_create(&t2, NULL, calculate_median, NULL);  
    pthread_create(&t3, NULL, calculate_stddev, NULL);  
  
    pthread_join(t1, NULL);  
    pthread_join(t2, NULL);  
    pthread_join(t3, NULL);  
  
    printf("\nResults:\n");  
    printf("Mean = %.2f\n", mean);  
    printf("Median = %.2f\n", median);  
    printf("Standard Deviation = %.2f\n", stddev);  
  
    free(numbers);  
    return 0;  
}  
  
void *calculate_mean(void *arg)  
{  
    double sum = 0;  
    for(int i = 0; i < count; i++)  
        sum += numbers[i];  
  
    mean = sum / count;  
    pthread_exit(0);  
}  
  
void *calculate_median(void *arg)  
{  
    int *temp = malloc(count * sizeof(int));  
  
    for(int i = 0; i < count; i++)  
        temp[i] = numbers[i];  
  
    qsort(temp, count, sizeof(int), compare_ints);  
  
    if(count % 2 == 0)  
        median = (temp[count/2] + temp[count/2 - 1]) / 2.0;  
    else  
        median = temp[count/2];  
  
    free(temp);  
    pthread_exit(0);  
}  
  
void *calculate_stddev(void *arg)  
{  
    double sum = 0;  
  
    for(int i = 0; i < count; i++)  
        sum += pow(numbers[i] - mean, 2);  
  
    stddev = sqrt(sum / count);  
    pthread_exit(0);  
}

---

# 🔄 WORKING (STEP-BY-STEP)

1. User inputs numbers
    
2. Three threads are created simultaneously
    
3. Each thread performs:
    
    - Mean thread → calculates average
        
    - Median thread → sorts and finds middle
        
    - Stddev thread → uses mean to calculate deviation
        
4. Main thread waits using `pthread_join()`
    
5. Results are printed
    

---

# 📤 OUTPUT (Example)

Enter the number of elements: 5  
Enter numbers:  
10 20 30 40 50  
  
Results:  
Mean = 30.00  
Median = 30.00  
Standard Deviation = 14.14

---

# 🧾 RESULT

The program was successfully executed using multithreading to compute mean, median, and standard deviation.

---

# ⚠️ IMPORTANT NOTE (EXAM TRAP)

👉 Standard deviation thread uses `mean`  
👉 But threads run **parallel**

💀 So technically:

- Stddev may run before mean is ready
    

👉 In real systems → use synchronization (mutex)  
👉 In lab → they ignore this

---

# ⚡ IMPORTANT POINTS

- Threads share global variables
    
- `pthread_create()` creates threads
    
- `pthread_join()` ensures completion
    
- Multithreading improves performance
    
- Data dependency can cause issues
    

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