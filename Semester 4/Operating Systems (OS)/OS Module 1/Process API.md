## **1. Introduction to Process API**

Process API is a set of **system calls** provided by the operating system to **create, execute, and manage processes**. These system calls enable interaction between user programs and the OS kernel.

The most fundamental system calls in UNIX-based systems are:

- `fork()` – Process creation
- `wait()` – Process synchronization
- `exec()` – Program execution

---

## **2. fork() System Call**

### **Definition**

`fork()` is used to create a **new process called the child process**, which is an exact duplicate of the parent process.

---

### **Working**

- When `fork()` is called:
    - A **new child process** is created.
    - The child gets a **copy of the parent’s address space**.
- Both parent and child execute **independently** from the next instruction.

---

### **Return Values**

- `0` → Returned in child process
- `>0` → Returned in parent (child PID)
- `-1` → Error in creation

---

### **Key Points**

- Both processes run **concurrently**
- Child inherits:
    - Code
    - Data
    - Open files

---

### **Example**

```
#include <stdio.h>  
#include <unistd.h>  
  
int main() {  
    int pid = fork();  
  
    if (pid == 0) {  
        printf("Child Process: PID = %d\n", getpid());  
    } else if (pid > 0) {  
        printf("Parent Process: PID = %d\n", getpid());  
    } else {  
        printf("Fork Failed\n");  
    }  
  
    return 0;  
}
```

---

## **3. wait() System Call**

### **Definition**

`wait()` is used by a parent process to **pause its execution until the child process terminates**.

---

### **Working**

- Parent process calls `wait()`
- Parent enters **waiting state**
- When child finishes:
    - OS notifies parent
    - Parent resumes execution

---

### **Return Value**

- Returns **PID of terminated child**
- Returns `-1` if no child exists

---

### **Key Points**

- Prevents **zombie processes**
- Ensures **proper synchronization**
- Used when parent depends on child’s result

---

### **Example**

```
#include <stdio.h>  
#include <unistd.h>  
#include <sys/wait.h>  
  
int main() {  
    int pid = fork();  
  
    if (pid == 0) {  
        printf("Child executing...\n");  
    } else {  
        wait(NULL);  
        printf("Parent resumes after child finishes\n");  
    }  
  
    return 0;  
}
```
---

## **4. exec() System Call**

### **Definition**

`exec()` replaces the **current process image** with a new program.

---

### **Working**

- The process calling `exec()`:
    - Loses its current code and data
    - Loads a new program into memory
- Execution starts from the new program’s entry point

---

### **Important Note**

- `exec()` **does not create a new process**
- If successful, it **never returns** to original code

---

### **Variants of exec()**

- `execl()`
- `execv()`
- `execvp()`
- `execle()`

---

### **Example**

```
#include <stdio.h>  
#include <unistd.h>  
  
int main() {  
    printf("Before exec\n");  
  
    execl("/bin/ls", "ls", NULL);  
  
    printf("This will not execute\n");  
  
    return 0;  
}
```

---

## 🔄 **Combined Working of fork(), exec(), and wait()**

### **Flow Explanation**

1. Parent process calls `fork()` → creates child
2. Child process may call `exec()` → loads a new program
3. Parent process calls `wait()` → waits for child to finish
4. Child terminates → parent resumes