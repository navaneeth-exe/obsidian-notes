## **Definition**

Mounting is the process of **attaching a file system to a directory (mount point)** so that its files become accessible in the existing directory tree.

---

## **Concept**

- UNIX has a **single hierarchical directory structure**
- Different file systems (disk, USB, etc.) are connected using **mounting**

👉 After mounting:

> Files appear as part of the normal directory tree

---

## **mount() System Call**

### **Syntax**

```
int mount(const char *source, const char *target,  
          const char *filesystemtype, unsigned long flags,  
          const void *data);
```

---

## **Parameters**

- `source` → device or file system (e.g., `/dev/sda1`)
- `target` → mount point (directory)
- `filesystemtype` → type (ext4, vfat, etc.)
- `flags` → options (read-only, etc.)
- `data` → additional info

---

### Steps:

1. Choose a **mount point** (empty directory)
2. Call `mount()` with device and directory
3. OS:
    - Reads file system metadata
    - Links it to mount point
4. Files become accessible through that directory

---

## **Example**

```
mount /dev/sda1 /mnt
```

👉 `/dev/sda1` is attached to `/mnt`

---

## **Before Mount**

- `/mnt` is empty

## **After Mount**

- `/mnt` contains files from `/dev/sda1`

---

## **Important Points**

- Mount point must be **empty directory**
- Mounted file system hides existing contents of that directory
- Supports multiple file systems in one tree

---

## **Unmounting**

👉 To detach:

```
umount /mnt
```

---

## **Key Points (WRITE FOR MARKS)**

- Mounting connects file system to directory
- Uses `mount()` system call
- Creates unified file system view
- Files accessed via mount point