## **Definition**

A function call is the process of **transferring control from one function (caller) to another function (callee)** to perform a specific task.

---

## **Basic Terms**

- **Caller Function** → Function that calls another function
- **Callee Function** → Function being called
- **Arguments** → Values passed to the function
- **Return Value** → Result returned back to caller

---

## **Working of Function Call**

1. Caller function passes **arguments**
2. Control transfers to **callee function**
3. Function executes required operations
4. Result is returned to caller
5. Execution resumes in caller function

---

## **Function Call in Assembly**

- Function call is done using:

```
JAL target
```

### **What JAL does:**

- Stores return address in **RA (return address register)**
- Jumps to the **target function**

---

## **Return from Function**

```
JR RA
```

👉 Returns control back to caller

---

## **Passing Arguments**

- Arguments are passed using **registers (a0, a1, …)**
- If more arguments → stored in **stack**

---

## **Return Value**

- Stored in **register a0**
- Sent back to caller

---

## **Role of Stack (VERY IMPORTANT 🔥)**

- Stores **return address**
- Stores **extra arguments**
- Stores **local variables**

👉 Stack follows **LIFO (Last In First Out)**

---

## **# **Function Call Example (C + Assembly)**

## **C Code Example**

```
```
int sum(int a, int b) {  
    int result;  
    result = a + b;  
    return result;  
}  
  
int main() {  
    int y;  
    y = sum(3, 4);  
    return 0;  
}
```
```

---

## **Explanation**

- `main()` → **caller function**
- `sum()` → **callee function**
- `3, 4` → arguments
- `y` → stores return value

---

## **Equivalent Assembly Code (RISC Style)**

```
main:  
    addi a0, zero, 3     # first argument  
    addi a1, zero, 4     # second argument  
    jal sum              # function call  
    addi s0, a0, 0       # store result in s0  
  
sum:  
    add s1, a0, a1       # s1 = a0 + a1  
    addi a0, s1, 0       # move result to a0  
    jr ra                # return to caller

```
---

## **Step-by-Step Working**

1. Arguments **3 and 4** stored in `a0`, `a1`
2. `jal sum`:
    - Saves return address in **ra**
    - Jumps to `sum`
3. Function adds values → result in `a0`
4. `jr ra` returns control
5. Result stored in `s0`

---

## **Key Points (Write this 💯)**

- Function call uses **JAL instruction**
- Return uses **JR RA**
- Arguments → `a0, a1`
- Return value → `a0`
---

## **Key Points (Write this 💯)**

- Uses **JAL and JR instructions**
- Arguments → registers
- Return value → a0
- Stack used for **storage and control**