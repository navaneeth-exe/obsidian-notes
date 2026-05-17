# 🎯 AIM

Create a new process using `fork()`. The child process should print **“PCCSL407”** and the parent process should print **“Operating Systems Lab”**. Use `wait()` to ensure the correct output order.

---

# 🧠 THEORY (EXPLANATION)

- `fork()` creates a **child process** from the parent.
    
- After `fork()`, both parent and child execute **independently**.
    
- Output order is **not guaranteed** unless controlled.
    
- `wait()` is used by the parent to:
    
    - Pause execution
        
    - Wait for the child to finish
        

👉 Without `wait()` → output can be random  
👉 With `wait()` → output becomes controlled

---

# ⚙️ ALGORITHM

1. Start
    
2. Include required header files
    
3. Call `fork()`
    
4. Check return value
    
5. If child process → print “PCCSL407”
    
6. If parent process → call `wait()` and print “Operating Systems Lab”
    
7. End
    

---

# ⚙️ CODE

```c 
#include<stdio.h>  
#include<sys/types.h>  
#include<unistd.h>  
#include<sys/wait.h>  
  
int main()  
{  
    pid_t pid;  
  
    pid = fork();   // Create a new process  
  
    if (pid < 0)  
    {  
        perror("fork failed");  
        return 1;  
    }  
    else if (pid == 0)  
    {  
        // Child process  
        printf("PCCSL407 ");  
    }  
    else  
    {  
        // Parent process  
        wait(NULL);   // Wait for child to finish  
        printf("Operating Systems Lab\n");  
    }  
  
    return 0;  
}
```

---

# 🔄 WORKING (STEP-BY-STEP)

1. Program starts
    
2. `fork()` creates a child process
    
3. Two processes now exist:
    
    - Child
        
    - Parent
        
4. Child executes:
    
    - Prints → **PCCSL407**
        
5. Parent executes:
    
    - Calls `wait()`
        
    - Waits for child to complete
        
    - Prints → **Operating Systems Lab**
        

---

# 📤 OUTPUT

```
PCCSL407 Operating Systems Lab
```

---

# 🧾 RESULT

The program was successfully executed using `fork()` and `wait()` to ensure proper execution order between parent and child processes.

---

# ⚡ IMPORTANT POINTS

- `fork()` creates a new process
    
- Child executes first (because of `wait()`)
    
- `wait()` ensures correct output order
    
- Without `wait()` → output may be unordered
    
- Parent and child run **concurrently**
    

---

# 🎤 VIVA QUESTIONS WITH ANSWERS

---

## 🔹 BASIC

### 1. What is fork()?

👉 A system call used to create a new process.

---

### 2. What is wait()?

👉 A system call that makes the parent wait for the child process.

---

### 3. What is a process?

👉 A program in execution.

---

### 4. What does fork() return?

👉

```
0 → child
> 0 → parent
< 0 → error
```

---

### 5. What is PID?

👉 Process ID.

---

## 🔹 INTERMEDIATE

### 6. Why is wait() used in this program?

👉 To ensure child prints first and maintain correct output order.

---

### 7. What happens without wait()?

👉 Output order becomes unpredictable.

---

### 8. Can parent and child run simultaneously?

👉 Yes.

---

### 9. How many processes are created?

👉 Two (parent + child)

---

### 10. Does fork() copy memory?

👉 Yes, it creates a duplicate process.

---

## 🔹 ADVANCED

### 11. What is a zombie process?

👉 A terminated process still in process table.

---

### 12. What is an orphan process?

👉 A process whose parent has terminated.

---

### 13. What is concurrent execution?

👉 Multiple processes executing at the same time.

---

### 14. What happens if fork() fails?

👉 Returns negative value.

---

### 15. What is getpid()?

👉 Returns process ID.

---

### 16. Why is synchronization needed?

👉 To control execution order.

---

### 17. Is execution order guaranteed without wait()?

👉 No.