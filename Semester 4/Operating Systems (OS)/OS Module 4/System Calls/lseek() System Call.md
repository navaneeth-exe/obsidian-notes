## **Definition**

`lseek()` is a system call used to **change the current file offset (position)** of an open file.

👉 It allows **random access** instead of sequential access.

---

## **Syntax**

```
off_t lseek(int fd, off_t offset, int whence);
```

- `fd` → file descriptor
- `offset` → number of bytes to move
- `whence` → reference point

---

## **Working**

- Every open file has a **file pointer (offset)**
- `lseek()` moves this pointer to a new position
- After that, `read()` or `write()` happens from that position

---

# **Three Modes of lseek() (VERY IMPORTANT)**

## **1. SEEK_SET**

- Offset is calculated from the **beginning of the file**

👉 New position = `offset`

### Example:

```
lseek(fd, 10, SEEK_SET);
```

👉 Moves pointer to **10th byte from start**

---

## **2. SEEK_CUR**

- Offset is calculated from the **current position**

👉 New position = current position + offset

### Example:

```
lseek(fd, 5, SEEK_CUR);
```

👉 Moves **5 bytes forward from current position**

---

## **3. SEEK_END**

- Offset is calculated from the **end of the file**

👉 New position = file size + offset

### Example:

```
lseek(fd, -10, SEEK_END);
```
👉 Moves to **10 bytes before end**

---

## **Important Points**

- Used for **random file access**
- Does not read/write data, only moves pointer
- Can move forward or backward
- Returns new file position