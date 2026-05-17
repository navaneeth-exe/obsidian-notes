# 🎯 **AIM**

To simulate address translation in a paging scheme using command line arguments:

- Virtual address space size (MB)
- Page size (KB)
- Virtual address (decimal)

and determine the corresponding physical address.

---

# 📚 **THEORY**

Paging is a memory management technique in which:

- Logical memory is divided into pages
- Physical memory is divided into frames

A page table maps:

```
Page Number → Frame Number
```

---

## 🔹 Address Translation

A virtual address contains:

```
Page Number + Offset
```

---

## 🔹 Formula

### Page Number

```
Page Number = Virtual Address / Page Size
```

### Offset

```
Offset = Virtual Address % Page Size
```


# 🧾 **ALGORITHM – Address Translation in Paging**

### Step 1:

Start

---

### Step 2:

Read three command line arguments:

- Virtual address space size (MB)
- Page size (KB)
- Virtual address

---

### Step 3:

Check whether correct number of arguments are provided.

- If not:
    - Display usage message
    - Stop program

---

### Step 4:

Convert command line arguments from string to integer using `atoi()`.

---

### Step 5:

Convert:

- Virtual address space from MB to bytes
- Page size from KB to bytes

---

### Step 6:

Calculate:

```
Number of Pages = Virtual Address Space / Page Size
```

---

### Step 7:

Create page table and assign frame numbers.

---

### Step 8:

Calculate:

```
Page Number = Virtual Address / Page Size
```

```
Offset = Virtual Address % Page Size
```

---

### Step 9:

Check whether page number exists in page table.

- If valid:
    - Obtain frame number from page table
    - Display:
        
        ```
        Physical Address = <Frame Number, Offset>
        ```
        
- Else:
    - Display:
        
        ```
        Page Table Miss
        ```
        

---

### Step 10:

Stop


---

# 💻 **PROGRAM**

```c title:addressTransaltion
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[]) {

    // Check command line arguments
    if (argc != 4) {
        printf("Usage: %s <VAS_MB> <PAGE_KB> <VIRTUAL_ADDRESS>\n", argv[0]);
        return 1;
    }

    // Read command line arguments
    int vas_mb = atoi(argv[1]);
    int page_kb = atoi(argv[2]);
    int virtual_address = atoi(argv[3]);

    // Convert sizes to bytes
    int vas_bytes = vas_mb * 1024 * 1024;
    int page_bytes = page_kb * 1024;

    // Calculate number of pages
    int num_pages = vas_bytes / page_bytes;

    // Page table
    int pageTable[num_pages];

    // Dummy page-to-frame mapping
    for (int i = 0; i < num_pages; i++) {
        pageTable[i] = i + 10;
    }

    // Calculate page number and offset
    int page_number = virtual_address / page_bytes;
    int offset = virtual_address % page_bytes;

    // Address translation
    if (page_number < num_pages) {

        int frame_number = pageTable[page_number];

        printf("Physical Address = <%d, %d>\n",
               frame_number,
               offset);
    }
    else {

        printf("Page Table Miss\n");
    }

    return 0;
}
```

---

# 📤 **COMPILATION & EXECUTION**

```
gcc paging.c -o paging
./paging 4 1 2050
```

---

# 📤 **SAMPLE OUTPUT**

```
Physical Address = <12, 2>
```

---

# 🔍 **DETAILED CODE EXPLANATION**

---

## 🔹 `argc` and `argv`

```
int main(int argc, char *argv[])
```

👉 Used for command line arguments.

- `argc` → number of arguments
- `argv[]` → stores arguments as strings

---

## 🔹 Argument Check

```
if (argc != 4)
```

👉 Program expects:

1. Program name
2. VAS size
3. Page size
4. Virtual address

---

## 🔹 `atoi()`

```
atoi(argv[1])
```

👉 Converts string → integer.

---

## 🔹 Convert into Bytes

```
vas_mb * 1024 * 1024
```

👉 Converts MB → bytes.

---

## 🔹 Page Number

```
page_number = virtual_address / page_bytes;
```

👉 Finds page containing address.

---

## 🔹 Offset

```
offset = virtual_address % page_bytes;
```

👉 Finds position inside page.

---

## 🔹 Page Table

```
pageTable[i] = i + 10;
```

👉 Dummy mapping:

```
Page 0 → Frame 10Page 1 → Frame 11
```

---

## 🔹 Physical Address

```
<frame_number, offset>
```

👉 Final translated address.

---

# ✅ **RESULT**

The address translation in paging scheme using command line arguments was successfully simulated.

---

# 🔥 **VIVA QUESTIONS**

---

## ❓ Why use command line arguments?

👉 To pass inputs during program execution.

---

## ❓ What is `argc`?

👉 Number of command line arguments.

---

## ❓ What is `argv[]`?

👉 Array storing command line arguments as strings.

---

## ❓ Why use `atoi()`?

👉 Converts string into integer.

---

## ❓ What is paging?

👉 Memory management using pages and frames.

---

## ❓ Formula for page number?

👉

```
Page Number = Address / Page Size
```

---

## ❓ Formula for offset?

👉

```
Offset = Address % Page Size
```