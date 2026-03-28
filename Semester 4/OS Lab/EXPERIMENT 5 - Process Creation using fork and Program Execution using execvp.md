# 🎯 AIM

To write a program to add two integers using command-line arguments and execute it through a child process created using `fork()` and replaced using `execvp()`.

---

# 🧠 THEORY (EXPLANATION)

### 🔹 What is a Process?

A **process** is a program in execution. Each process has:

- Its own memory
    
- Its own execution state
    
- A unique Process ID (PID)
    

---

### 🔹 fork() System Call

- Used to **create a new process**
    
- The new process is called the **child process**
    
- The original process is called the **parent process**
    

👉 After `fork()`:

- Both processes run **simultaneously**
    
- Both execute the same code
    

---

### 🔹 Return Values of fork()

|Return Value|Meaning|
|---|---|
|`< 0`|Error|
|`0`|Child process|
|`> 0`|Parent process (returns child PID)|

---

### 🔹 execvp() System Call

- Used to **replace the current process memory**
    
- Loads a new program into the process
    

👉 Important:

- It **does NOT create a new process**
    
- It **overwrites the current process**
    

---

### 🔹 wait() System Call

- Used by parent process
    
- Waits for child to finish execution
    
- Prevents **zombie processes**
 --- 
# 🧾 ALGORITHM
## 🔹 Program 1: Addition Program (myadder)
Step 1: Start
Step 2: Read two integers from command-line arguments
Step 3: Convert arguments to integers using atoi()
Step 4: Add the two numbers
Step 5: Display the result
Step 6: Stop

## 🔹 Program 2: fork() + execvp()
Step 1: Start
Step 2: Call fork() system call
Step 3: Check return value
     If < 0 → Error
     If == 0 → Child process
     If > 0 → Parent process
Step 4 (Child Process):
    Execute myadder using execvp()
    Pass two integers as arguments
Step 5: If execvp() fails, print error
Step 6 (Parent Process):
    Wait for child using wait()
Step 7: Stop

---

# ⚙️ PROGRAM – 1 (myadder)

## 🔹 Explanation

- Takes input from command-line
    
- Converts strings → integers
    
- Adds values
    
- Displays result
    

---

## 🔹 Code

```
#include<stdio.h>  
#include<stdlib.h>  
  
int main(int argc, char *argv[])  
{  
    if(argc != 3)  
    {  
        printf("Usage: %s num1 num2\n", argv[0]);  
        return 1;  
    }  
  
    int a = atoi(argv[1]);  
    int b = atoi(argv[2]);  
  
    int sum = a + b;  
  
    printf("Sum = %d\n", sum);  
  
    return 0;  
}
```
---

## 🔹 Explanation of Key Parts

- `argc` → number of arguments
    
- `argv[]` → array storing arguments
    
- `atoi()` → converts string to integer
    

Example:

./myadder 10 20

👉 Output:

Sum = 30

---

# ⚙️ PROGRAM – 2 (fork + execvp)

## 🔹 Explanation

- Parent creates child using `fork()`
    
- Child replaces itself with `myadder`
    
- Parent waits for child
    

---

## 🔹 Code

```
#include<stdio.h>  
#include<unistd.h>  
#include<sys/types.h>  
#include<stdlib.h>  
#include<sys/wait.h>  
  
int main()  
{  
    pid_t pid;  
  
    pid = fork();  
  
    if(pid < 0)  
    {  
        perror("Fork failed");  
        return 1;  
    }  
    else if(pid == 0)  
    {  
        printf("Child Process (PID: %d)\n", getpid());  
  
        char *args[] = {"./myadder", "10", "20", NULL};  
  
        execvp(args[0], args);  
  
        perror("execvp failed");  
        exit(1);  
    }  
    else  
    {  
        printf("Parent Process (PID: %d), Child PID: %d\n", getpid(), pid);  
  
        wait(NULL);  
  
        printf("Child process finished.\n");  
    }  
  
    return 0;  
}
```
---

# 🔄 WORKING (STEP-BY-STEP)

1. Program starts
    
2. `fork()` creates child process
    
3. Two processes now exist:
    
    - Parent
        
    - Child
        
4. Child process:
    
    - Calls `execvp()`
        
    - Loads `myadder`
        
    - Executes addition
        
5. Parent process:
    
    - Waits using `wait()`
        
    - Prints completion message
        

---

# 📤 OUTPUT

```
Parent Process (PID: 1234), Child PID: 1235  
Child Process (PID: 1235)  
Sum = 30  
Child process finished.
```

---

# 🧾 RESULT

The program was successfully executed to demonstrate process creation using `fork()` and process replacement using `execvp()`.

---

# ⚡ IMPORTANT CONCEPTS (REVISION GOLD)

- `fork()` → creates process
    
- `execvp()` → replaces process
    
- `wait()` → synchronization
    
- Parent & child run **concurrently**
    
- `execvp()` never returns on success
    

---

# 🎤 VIVA QUESTIONS WITH ANSWERS (FULL SET)

---

## 🔹 BASIC LEVEL

### 1. What is a process?

👉 A program in execution.

---

### 2. What is fork()?

👉 A system call used to create a new process.

---

### 3. What is execvp()?

👉 A system call that replaces the current process with a new program.

---

### 4. What is PID?

👉 Process ID — unique identifier for each process.

---

### 5. What does fork() return?

👉

- 0 → child
    
- > 0 → parent
    
- <0 → error
    

---

## 🔹 INTERMEDIATE LEVEL

### 6. Difference between fork() and exec()?

👉 fork creates new process, exec replaces process.

---

### 7. Why is NULL used in execvp()?

👉 To indicate end of argument list.

---

### 8. What happens if execvp() succeeds?

👉 It does not return.

---

### 9. Why is wait() used?

👉 To wait for child and prevent zombie process.

---

### 10. Can parent and child run simultaneously?

👉 Yes, they run concurrently.

---

## 🔹 ADVANCED LEVEL

### 11. What is a zombie process?

👉 A terminated process still in process table.

---

### 12. What is an orphan process?

👉 A process whose parent has terminated.

---

### 13. What is copy-on-write?

👉 Memory is shared until modified after fork.

---

### 14. Difference between execvp() and execl()?

👉

- execvp → uses array
    
- execl → uses list
    

---

### 15. What happens if fork() fails?

👉 Returns negative value.

---

### 16. Does execvp() create a new process?

👉 No, it replaces the current process.

---

### 17. What happens to variables after fork()?

👉 Each process has its own copy.

---

### 18. What is system call?

👉 Interface between user program and OS.

---

### 19. What happens without wait()?

👉 Zombie processes may occur.

---

### 20. What is getpid()?

👉 Returns process ID.

---

# 🧠 FINAL ONE-LINER

👉 `fork()` creates a child process, `execvp()` replaces it with another program, and `wait()` ensures proper execution order.