## **1. Hard Link**

## **Definition**

A **hard link** is a directory entry that points **directly to the same inode (file data)** as another file.

👉 Basically:

> Two names → same actual file

---

## **Concept**

- Files are stored using **inodes**
- Hard link creates another name pointing to **same inode**

---

## **Working**
👉 Both filenames share:

- Same inode
- Same data


---

## **Key Features**

- No original vs copy
- Changes reflect in both
- File exists until all links are deleted

---

## **Limitations**

- Cannot link directories (usually)
- Cannot cross file systems

---

---

# **2. Soft Link (Symbolic Link)**

## **Definition**

A **soft link** is a file that contains the **path (name) of another file**.

👉 Basically:

> Shortcut to another file

---

## **Concept**

- It stores **path**, not actual data reference
- Works like a pointer

---

## **Working**

👉 Soft link → points to filename → then inode

---

## **Key Features**

- Works across file systems
- Can link directories
- Separate inode

---

## **Problem**

- If original file deleted →  
    👉 **Broken link (dangling link)** 😬

---

---

# **Difference Between Hard Link and Soft Link**

|Feature|Hard Link|Soft Link|
|---|---|---|
|Reference|Same inode|Path to file|
|Inode|Same|Different|
|File systems|Not allowed across FS|Allowed|
|If original deleted|Still works|Broken link|
|Directories|Not allowed|Allowed|
|Storage|No extra space|Small extra space|

---

## **Important Points (WRITE FOR MARKS)**

- Hard link → inode-based
- Soft link → path-based
- Hard link safe, soft link flexible
- Soft link can become **dangling**