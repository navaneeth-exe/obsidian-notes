## **What does `mkdir()` create?**

The `mkdir()` system call is used to **create a new directory** in the file system.

👉 It:

- Creates a directory entry
- Allocates an inode
- Initializes the directory structure

---

## **Syntax**

int mkdir(const char *pathname, mode_t mode);

- `pathname` → name/path of directory
- `mode` → permissions

---

# **Default Entries in a New Directory**

Every newly created directory contains **two special entries**:

---

## **1. `.` (dot)**

- Refers to the **current directory itself**

---

## **2. `..` (dot dot)**

- Refers to the **parent directory**

---

## **Important Points**

- These entries are created **automatically by OS**
- Help in **directory navigation**
- Even an empty directory contains these two entries