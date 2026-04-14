## **Definition**

A stack is a special area of memory used to **store temporary data during program execution**, especially during function calls.

---

## **Basic Concept**

- Stack follows **LIFO (Last In First Out)**
- Last inserted element is removed first

---

## **Stack Pointer (SP)**

- A special register that holds the **address of the top of the stack**
- Stack grows/shrinks based on push and pop operations

---

## **Operations on Stack**

### **1. PUSH**

- Adds data to the stack
- Stack pointer is updated

### **2. POP**

- Removes data from the stack
- Stack pointer is updated

---

## **Functions of Stack (VERY IMPORTANT 🔥)**

### **1. Storing Return Address**

- When a function is called, return address is saved
- Helps to return back after execution

---

### **2. Passing Arguments**

- If registers are full, extra arguments are stored in stack

---

### **3. Storing Local Variables**

- Variables inside a function are stored temporarily
- Removed after function ends

---

## **Working (Function Call Context)**

1. Function call occurs
2. Return address pushed to stack
3. Arguments/local variables stored
4. Function executes
5. Return address popped
6. Control goes back to caller

---

## **Key Points (Write this 💯)**

- Follows **LIFO principle**
- Uses **Stack Pointer (SP)**
- Operations: **Push and Pop**
- Used in **function calls and memory management**