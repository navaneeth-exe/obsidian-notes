## **Definition**

Memory API refers to the set of **system calls and library functions** used to **allocate, manage, and release memory** during program execution.

---

## **Types of Memory Allocation**

- **Static allocation** → compile-time
- **Dynamic allocation** → runtime (using memory API)

---

# **Main Memory API Functions**

---


### Refer screenshot
## **1. malloc()**

### **Definition**

Allocates a block of memory of specified size.

```
void *malloc(size_t size);
```

### **Features**

- Returns pointer to allocated memory
- Memory is **uninitialized**

---

## **2. calloc()**

### **Definition**

Allocates memory for multiple elements and initializes to zero.
```
void *calloc(size_t n, size_t size);
```

### **Features**

- Allocates `n × size` bytes
- Initializes memory to **0**

---

## **3. realloc()**

### **Definition**

Resizes previously allocated memory.

```
void *realloc(void *ptr, size_t new_size);
```

### **Features**

- Expands or shrinks memory
- May move memory location

---

## **4. free()**

### **Definition**

Releases allocated memory back to system.

```
void free(void *ptr);
```
---

# **Example**

```
int *arr = (int*) malloc(5 * sizeof(int));  
arr = realloc(arr, 10 * sizeof(int));  
free(arr);
