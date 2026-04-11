The three main system calls used to read a directory are:

1. **`opendir()`**  
    👉 Opens a directory stream
2. **`readdir()`**  
    👉 Reads entries from the directory one by one
3. **`closedir()`**  
    👉 Closes the directory stream

---

# **What does `struct dirent` contain?**

`struct dirent` is a structure used to represent a **directory entry** returned by `readdir()`.

---

## **Definition**

👉 It stores information about each file/subdirectory inside a directory.

---

## **Common Fields**

```
struct dirent {  
    ino_t d_ino;        // inode number  
    char  d_name[];     // file name  
};
```
---

## **Additional Fields (may vary by system)**

- `d_type` → type of file (file, directory, etc.)
- `d_reclen` → length of record

---

## **Working**

- `readdir()` returns a pointer to `struct dirent`
- Each call gives **one directory entry**
- Loop is used to read all entries

---

## **Example**

```
DIR *d = opendir(".");  
struct dirent *dir;  
  
while ((dir = readdir(d)) != NULL) {  
    printf("%s\n", dir->d_name);  
}  
  
closedir(d);
```
---

## **Key Points (WRITE FOR MARKS)**

- `opendir()` → open directory
- `readdir()` → read entries
- `closedir()` → close directory
- `struct dirent` stores file info