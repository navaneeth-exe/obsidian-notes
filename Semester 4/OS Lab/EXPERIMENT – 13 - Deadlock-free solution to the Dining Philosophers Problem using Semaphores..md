## 🎯 **AIM**

To implement a deadlock-free solution for the Dining Philosophers problem using semaphores.

---

## 📚 **THEORY**

The Dining Philosophers problem is a classical synchronization problem.

- There are **N philosophers** sitting around a table
- Each philosopher needs **two chopsticks** to eat
- Chopsticks are shared between neighbors

### 🔹 Problem:

- If all philosophers pick one chopstick → **deadlock occurs**

---

### 🔹 Solution Used:

- Use **semaphores**
- Use a **mutex semaphore (N-1)** to limit philosophers entering critical section

👉 This ensures:

- At least one philosopher can eat
- Deadlock is avoided

---

# 🧾 **CORRECT ALGORITHM**

**Step 1:** Start

**Step 2:** Initialize:

- Number of philosophers `N`
- Create `N` chopstick semaphores initialized to 1
- Create a mutex semaphore initialized to `N-1`

---

**Step 3:** Create `N` philosopher threads

---

**Step 4:** Each philosopher repeats forever:

- Think (sleep for some time):
	Philosopher thinks for some time
- Wait on mutex semaphore
    sem_wait(mutex)
		This allows only `N−1` philosophers to compete for chopsticks simultaneously.
    
- Pick up left chopstick
    
    sem_wait(chopstick[i])
    
- Pick up right chopstick
    
    sem_wait(chopstick[(i+1)%N])
    
- Eating
	 Philosopher eats for some time
- Release left chopstick
    
    sem_post(chopstick[i])
    
- Release right chopstick
    
    sem_post(chopstick[(i+1)%N])
    
- Signal mutex
	    Leave critical section
    sem_post(mutex)
    

---

**Step 5:** Repeat

**Step 6:** Stop

---

# 💻 **PROGRAM**

```


#include <stdio.h>  
#include <stdlib.h>  
#include <pthread.h>  
#include <semaphore.h>  
#include <unistd.h>  
  
#define N 5  
  
sem_t chopstick[N];  
sem_t mutex;  
  
void *philosopher(void *num) {  
    int id = *(int *)num;  
  
    while (1) {  
        printf("Philosopher %d is thinking\n", id);  
        sleep(1);  
  
        sem_wait(&mutex);  
  
        sem_wait(&chopstick[id]);  
        sem_wait(&chopstick[(id + 1) % N]);  
  
        printf("Philosopher %d is eating\n", id);  
        sleep(2);  
  
        sem_post(&chopstick[id]);  
        sem_post(&chopstick[(id + 1) % N]);  
  
        sem_post(&mutex);  
  
        printf("Philosopher %d finished eating\n", id);  
        sleep(1);  
    }  
}  
  
int main() {  
    pthread_t tid[N];  
    int philosopher_id[N];  
  
    sem_init(&mutex, 0, N - 1);  
  
    for (int i = 0; i < N; i++)  
        sem_init(&chopstick[i], 0, 1);  
  
    for (int i = 0; i < N; i++) {  
        philosopher_id[i] = i;  
        pthread_create(&tid[i], NULL, philosopher, &philosopher_id[i]);  
    }  
  
    for (int i = 0; i < N; i++)  
        pthread_join(tid[i], NULL);  
  
    for (int i = 0; i < N; i++)  
        sem_destroy(&chopstick[i]);  
  
    sem_destroy(&mutex);  
  
    return 0;  
}
```

---

## 📤 **OUTPUT (Sample)**

Philosopher 0 is thinking  
Philosopher 1 is thinking  
Philosopher 2 is eating  
Philosopher 3 is thinking  
Philosopher 4 is eating  
...


---

# **DETAILED CODE EXPLANATION – DINING PHILOSOPHERS**

---

## 🔹 **HEADER FILES**

```
#include <stdio.h>  
#include <stdlib.h>  
#include <pthread.h>  
#include <semaphore.h>  
#include <unistd.h>
```
### Why each:

- `stdio.h` → `printf`
- `stdlib.h` → general functions
- `pthread.h` → threads (`pthread_create`)
- `semaphore.h` → semaphores (`sem_wait`, `sem_post`)
- `unistd.h` → `sleep()`

---

# 🔹 **MACRO**

```
#define N 5
```

👉 Total philosophers = 5  
👉 Also number of chopsticks = 5

---

# 🔹 **SEMAPHORES**

```
sem_t chopstick[N];  
sem_t mutex;
```

### Meaning:

- `chopstick[i]` → semaphore for each chopstick
- `mutex` → controls how many philosophers can try eating

---

# 🔹 **PHILOSOPHER FUNCTION**

```
void *philosopher(void *num)
```

👉 Each thread runs this function

---

## 🔹 **GET PHILOSOPHER ID**

```
int id = *(int *)num;
```

👉 Converts pointer to integer ID

---

# 🔁 **INFINITE LOOP**

```
while (1)
```

👉 Philosophers continuously:

- Think → Eat → Repeat

---

## 🧠 **THINKING STATE**

```
printf("Philosopher %d is thinking\n", id);  
sleep(1);
```
👉 Simulates thinking

---

# 🚪 **ENTRY SECTION (CRITICAL PART)**

```
sem_wait(&mutex);
```

👉 This is the **deadlock prevention trick**

### What it does:

- Allows only **N-1 philosophers (4)** to try eating
- Prevents all 5 from grabbing one chopstick

💀 Without this → DEADLOCK

---

# 🍴 **PICK UP CHOPSTICKS**

```
sem_wait(&chopstick[id]);  
sem_wait(&chopstick[(id + 1) % N]);
```
### Explanation:

- Left chopstick → `id`
- Right chopstick → `(id + 1) % N`

👉 `% N` ensures circular table

---

## 💡 Example:

For philosopher 4:

```
Left = chopstick[4]  
Right = chopstick[(4+1)%5] = chopstick[0]
```

---

# 🍽️ **EATING SECTION**

```
printf("Philosopher %d is eating\n", id);  
sleep(2);
```

👉 Simulates eating

---

# 🔄 **PUT DOWN CHOPSTICKS**

```
sem_post(&chopstick[id]);  
sem_post(&chopstick[(id + 1) % N]);
```

👉 Releases both chopsticks

---

# 🚪 **EXIT SECTION**

```
sem_post(&mutex);
```

👉 Allows another philosopher to enter

---

# 🔁 **BACK TO THINKING**
```
printf("Philosopher %d finished eating\n", id);  
sleep(1);
```

---

# 🚀 **MAIN FUNCTION**

---

## 🔹 **THREAD DECLARATION**

```
pthread_t tid[N];  
int philosopher_id[N];
```
- `tid[]` → thread IDs
- `philosopher_id[]` → store IDs

---

# 🔹 **INITIALIZE MUTEX**

```
sem_init(&mutex, 0, N - 1);
```

👉 Key logic:

- Only **4 philosophers allowed at once**

💀 This avoids deadlock completely

---

# 🔹 **INITIALIZE CHOPSTICKS**

```
sem_init(&chopstick[i], 0, 1);
```

👉 Each chopstick = binary semaphore (1)

---

# 🔹 **CREATE THREADS**

```
pthread_create(&tid[i], NULL, philosopher, &philosopher_id[i]);
```

👉 Creates philosopher threads

---

# 🔹 **JOIN THREADS**

```
pthread_join(tid[i], NULL);
```

👉 Keeps program running (threads never end)

---

# 🔹 **DESTROY SEMAPHORES**

```
sem_destroy(&chopstick[i]);  
sem_destroy(&mutex);
```

👉 Cleanup (not reached due to infinite loop)

---

# 🧠 **HOW DEADLOCK IS PREVENTED**

### Normal problem:

- 5 philosophers → each picks 1 chopstick
- Everyone waits → deadlock 💀

---

### Your solution:

- Only 4 allowed (`mutex = N-1`)
- One philosopher always gets both chopsticks

👉 So system never gets stuck
---

## ✅ **RESULT**

The Dining Philosophers problem was successfully implemented using semaphores, and deadlock was avoided by limiting concurrent access.

---

# 🔥 **VIVA QUESTIONS**

## 🧠 Basic

1. What is Dining Philosophers problem?  
    👉 Synchronization problem with shared resources
2. What is deadlock?  
    👉 Processes waiting indefinitely

---

## ⚙️ Conceptual

3. Why deadlock occurs here?  
    👉 Each philosopher holds one chopstick
4. How is deadlock avoided?  
    👉 Allow only N-1 philosophers

---

## 🧮 Technical

5. What is semaphore?  
    👉 Synchronization tool
6. Difference between sem_wait and sem_post?  
    👉 wait → decrement  
    👉 post → increment

---

## 💀 Advanced

7. Why mutex = N-1?  
    👉 Ensures at least one philosopher can eat
8. Can starvation occur?  
    👉 Yes (in some cases)

---

## 🧠 PRO LINE 😎

> “Deadlock is prevented by limiting the number of philosophers competing for resources using a semaphore.”