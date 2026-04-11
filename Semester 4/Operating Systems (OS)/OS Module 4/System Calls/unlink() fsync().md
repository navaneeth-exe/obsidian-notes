## **Definition**

`unlink()` is a system call used to **remove (delete) a file name from the file system**.

👉 It removes the **directory entry**, not necessarily the file data immediately.

---

## **Syntax**

```
int unlink(const char *pathname);
```

---

## **Working**

- OS removes the **link (name → inode)**
- Decreases the **link count** of the file
- If link count becomes **0**:
    - File is deleted
    - Disk space is freed

---

## **Important Concept**

👉 A file is actually deleted **only when:**

- Link count = 0
- AND no process is using it

💡 So:

> Even after `unlink()`, file may still exist if it’s open

---

## **Example**

```
unlink("file.txt");
```

👉 Removes file from directory

---

## **Key Points**

- Deletes file name (not immediate data)
- Works on links (hard links concept)
- File removed when no references exist

---

## **One-Line Conclusion**

👉 _`unlink()` removes a file name from the file system and deletes the file when no references remain._

---

# **fsync() System Call**

## **Definition**

`fsync()` is used to **flush all modified data of a file from memory to disk**.

👉 Ensures data is **physically written to storage**

---

## **Syntax**

```
int fsync(int fd);
```

---

## **Working**

- OS normally keeps data in **buffer/cache**
- `fsync()` forces:
    - File data
    - Metadata (sometimes)  
        👉 to be written to disk immediately

---

## **Why Needed**

- Prevent data loss during:
    - Power failure ⚡
    - System crash 💥

---

## **Example**
```
fsync(fd);
```

👉 Ensures all changes are saved to disk

---

## **Key Points**

- Forces disk write
- Improves reliability
- Slower than normal write
- Used in critical systems (databases, logs)

---

## **One-Line Conclusion**

👉 _`fsync()` ensures that all buffered file data is written to disk, providing data consistency and durability._