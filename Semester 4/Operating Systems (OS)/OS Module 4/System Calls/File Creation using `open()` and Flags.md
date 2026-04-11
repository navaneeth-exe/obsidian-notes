## **Definition**

File creation in UNIX-based systems is done using the **`open()` system call**, where a file can be created if it does not exist by using specific flags.

---

## **Syntax**

int fd = open("filename", flags, mode);

- `filename` → name of the file
- `flags` → control how file is opened
- `mode` → permissions (used only when creating file)

---

## **Working**

When a process calls `open()`:

1. The OS checks whether the file already exists
2. If the file does not exist and `O_CREAT` flag is used → a new file is created
3. OS allocates:
    - an **inode (metadata)**
    - a **directory entry**
4. The file is added to the **open file table**
5. A **file descriptor (integer)** is returned to the process

---

## **Important Flags**

- `O_RDONLY` → open file in read-only mode
- `O_WRONLY` → open file in write-only mode
- `O_RDWR` → open file for both reading and writing
- `O_CREAT` → create file if it does not exist
- `O_EXCL` → used with `O_CREAT`, gives error if file already exists
- `O_TRUNC` → deletes existing content of file
- `O_APPEND` → writes data at the end of file

---

## **Example**

```
int fd = open("data.txt", O_CREAT | O_WRONLY, 0644);
```

👉 Meaning:

- Create file if not exists
- Open in write mode
- Permission = **rw-r--r--**

---

## **Special Cases**

- If file exists and `O_CREAT` is used → file is opened normally
- If `O_CREAT | O_EXCL` is used → error if file exists
- If `O_TRUNC` is used → file content becomes empty
- If `O_APPEND` is used → writing always happens at end

---

## **Key Points**

- `open()` is used for both opening and creating files
- File is created only when `O_CREAT` is specified
- OS manages inode and directory entry
- File descriptor is returned for further operations