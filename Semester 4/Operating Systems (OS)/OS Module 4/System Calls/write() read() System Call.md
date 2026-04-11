## **What does write() do?**

The `write()` system call is used to **write data from a process to a file or device**.

👉 It copies data from **user buffer → file (kernel space → disk)**

---

## **Syntax**

```
ssize_t write(int fd, const void *buf, size_t count);
```

---

## **What does it return?**

- Returns **number of bytes actually written**
- Returns **-1** if an error occurs

👉 Important:

> It may write **less than requested bytes**

---

---

# **read() System Call**

## **What does read() do?**

The `read()` system call is used to **read data from a file or device into a buffer**.

👉 It copies data from **file → user buffer**

---

## **Syntax**

```
ssize_t read(int fd, void *buf, size_t count);
```

---

## **Three Arguments**

1. **fd (file descriptor)**
    - Identifies the file to read from
2. **buf (buffer)**
    - Memory where data will be stored
3. **count (size)**
    - Number of bytes to read

---

## **Return Value**

- Number of bytes actually read
- **0 → End of file (EOF)**
- **-1 → Error**

---

## **Key Points (WRITE FOR MARKS)**

- `write()` → buffer → file
- `read()` → file → buffer
- Both use **file descriptor**
- Return number of bytes processed

---

## **One-Line Conclusion**

👉 _`write()` sends data to a file, while `read()` retrieves data from a file using a file descriptor and buffer._