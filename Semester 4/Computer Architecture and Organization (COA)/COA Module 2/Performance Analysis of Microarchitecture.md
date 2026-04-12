## **1. Execution Time**

### **Definition**

Execution time is the **total time taken to complete one instruction or one program**.


# **Execution Time Equation (Exam Answer)**

$$
Execution Time=Number of Instructions×Cycles per Instruction (CPI)×Clock Cycle Time
$$


## **Alternative Form**


Execution Time= Instrcution Count * CPI / clock rate
### **Key Idea**


- Measures **latency** (how fast one instruction finishes)

---

### **For Different Architectures**

#### **Single Cycle**

- One instruction per cycle
- **Execution Time = 1 long clock cycle**
- Slow because cycle is very long

---

#### **Multi Cycle**

- One instruction takes **multiple cycles**
- **Execution Time = multiple short cycles**
- Faster than single cycle

---

#### **Pipelined**

- Instruction still takes multiple stages
- But stages are overlapped
- **Execution time per instruction ≈ same as multi-cycle**

---

## **2. Throughput**

### **Definition**

Throughput is the **number of instructions completed per unit time**.

### **Key Idea**

- Measures **overall performance (how many instructions executed)**

---

### **For Different Architectures**

#### **Single Cycle**

- 1 instruction per cycle
- Low throughput (long cycle time)

---

#### **Multi Cycle**

- Takes multiple cycles per instruction
- Moderate throughput

---

#### **Pipelined**

- Multiple instructions executed in parallel
- **High throughput (1 instruction per cycle ideally)**