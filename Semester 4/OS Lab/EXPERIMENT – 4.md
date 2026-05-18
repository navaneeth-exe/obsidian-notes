## 📝 **Experiment Name**

Creation of a new process using `fork()` system call and displaying parent and child process IDs. Also, to observe the process hierarchy using `pstree`.

---

## 🎯 **AIM**

To create a child process using the `fork()` system call, print the process IDs of parent and child, and display the process tree using the `pstree` command.

---

## 📚 **THEORY**

In Linux/Unix systems, a new process is created using the **`fork()` system call**.

- `fork()` creates a **child process** which is an exact copy of the parent.
- After `fork()`:
    - Parent and child execute **independently**
    - Both continue execution from the next line

### 🔹 Return values of `fork()`

- `0` → returned to **child process**
- `>0` → returned to **parent process** (child PID)
- `<0` → error in process creation

### 🔹 Process IDs

- `getpid()` → returns process ID
- `getppid()` → returns parent process ID

### 🔹 `pstree` Command

- Displays process hierarchy in **tree format**
- Helps visualize parent-child relationships
- Root process is usually **init/systemd (PID 1)**

---

## 🧾 **ALGORITHM**

**Step 1:** Start  
**Step 2:** Include required header files  
**Step 3:** Call `fork()` system call  
**Step 4:** Check return value of `fork()`  
**Step 5:** If child process, print PID and PPID  
**Step 6:** If parent process, print PID and child PID  
**Step 7:** Use `sleep()` to keep processes alive  
**Step 8:** Use `pstree` command to observe process tree  
**Step 9:** Stop

---

## 💻 **PROGRAM**

```c
#include<stdio.h>  
#include<unistd.h>  
#include<sys/types.h>  
  
int main()  
{  
    pid_t pid;  
  
    pid = fork();  
  
    if (pid < 0)  
    {  
        perror("Fork failed");  
        return 1;  
    }  
    else if (pid == 0)  
    {  
        printf("Child Process:\n");  
        printf(" PID = %d\n", getpid());  
        printf(" PPID = %d\n", getppid());  
  
        sleep(30); // keep child alive  
    }  
    else  
    {  
        printf("Parent Process:\n");  
        printf(" PID = %d\n", getpid());  
        printf(" Child PID = %d\n", pid);  
  
        sleep(30); // keep parent alive  
    }  
  
    return 0;  
}
```

---

# 🔍 **DETAILED EXPLANATION OF THE CODE**

### 🔹 Header Files

- `stdio.h` → for input/output functions
- `unistd.h` → contains `fork()`, `getpid()`, `sleep()`
- `sys/types.h` → defines `pid_t`

---

### 🔹 Variable Declaration

```
pid_t pid;
```

- `pid_t` → data type used to store process IDs

---

### 🔹 Creating a Process

```
pid = fork();
```

- Creates a **new child process**
- After this:
    - Two processes run simultaneously

---

### 🔹 Error Handling

```
if (pid < 0)
```

- If fork fails → prints error

---

### 🔹 Child Process Block

```
else if (pid == 0)
```

- Executes only in child process

```
getpid()
```

- Returns **child’s PID**

```
getppid()
```

- Returns **parent’s PID**

---

### 🔹 Parent Process Block

else

- Executes in parent

```
getpid()
```

- Returns **parent PID**

```
pid
```

- Contains **child PID**

---

### 🔹 Sleep Function

```
sleep(30);
```

- Keeps process alive for 30 seconds
- Needed to:
    - Observe process using `pstree`

---

## 🖥️ **USING `pstree`**

Run in terminal:

```
pstree -p
```

### What you’ll see:

- Parent process
- Child process under it
- Full hierarchy from init/systemd

---

## 📤 **OUTPUT**

```
Parent Process:  
 PID = 1234  
 Child PID = 1235  
  
Child Process:  
 PID = 1235  
 PPID = 1234
```

---

## ✅ **RESULT**

The program was successfully executed. A child process was created using `fork()`, and the process hierarchy was observed using the `pstree` command.

---

# 🔥 **VIVA QUESTIONS**

## 🧠 Basic

1. What is `fork()`?  
    👉 System call used to create a new process
2. What is PID?  
    👉 Unique identifier of a process
3. What is PPID?  
    👉 Parent process ID

---

## ⚙️ Conceptual

4. What does `fork()` return?  
    👉 0 → child  
    👉 >0 → parent  
    👉 <0 → error
5. What is process duplication?  
    👉 Child is copy of parent
6. Do parent and child run simultaneously?  
    👉 Yes

---

## 🧮 Technical

7. Why use `sleep()`?  
    👉 To keep process alive for observation
8. What is `pid_t`?  
    👉 Data type for process ID
9. What is `pstree`?  
    👉 Command to display process hierarchy

---

## 💀 Advanced (examiner traps)

10. Can parent execute before child?  
    👉 Yes, execution order is not guaranteed
11. What happens if parent exits early?  
    👉 Child becomes **orphan process**
12. What is an orphan process?  
    👉 Process whose parent has terminated
13. What is init/systemd?  
    👉 First process (PID 1) that adopts orphan processes