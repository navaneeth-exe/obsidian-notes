# 🧠 **Pipeline Hazard (for exam)**

## ✅ **Definition**

A **pipeline hazard** is a condition in a pipelined processor where the normal flow of instruction execution is disrupted, causing incorrect results or delays.

> It occurs when instructions in the pipeline depend on each other or compete for resources.

---

# ⚙️ **Why it occurs**

In pipelining, multiple instructions execute simultaneously in different stages (IF, ID, EX, MEM, WB).  
But sometimes:

- Data is not ready
- Resources are busy
- Control flow changes

👉 This leads to hazards.



# ⚡ 1. DATA HAZARD (FORWARDING)

## 💻 Code:

```
addi x1, x0, 10  
addi x2, x0, 5  
add x3, x1, x2  
sub x4, x3, x2

```
---

## 🎬 While stepping execution

👉 Point to pipeline

### 💬 SAY:

> “The add instruction goes through IF, ID, EX, MEM, and WB stages.”

> “The result of add is generated in the EX stage but officially written in the WB stage.”

---

👉 Point to next instruction (`sub`)

> “The sub instruction needs the result of add during its EX stage.”

---

## 🔥 KEY LINE (VERY IMPORTANT)

> “But at that time, the result is still in the pipeline and not yet written back.”

---

👉 Point at datapath forwarding line

> “So the processor forwards the result from the MEM stage of the add instruction to the EX stage of the sub instruction.”

---

## ✅ FINAL LINE

> “This is called data forwarding, and it avoids a pipeline stall.”

# 🧠 **Data Forwarding (in Pipeline)**

## ✅ **Definition**

**Data forwarding** is a technique used in pipelined processors to resolve data hazards by **sending the result of an instruction directly from a later stage to an earlier stage**, without waiting for it to be written back to the register.

---

# ⚡ 2. LOAD-USE HAZARD (STALL)

## 💻 Code:

```
addi x2, x0, 0  
lw x1, 0(x2)  
add x3, x1, x2
```

---

## 🎬 Step execution slowly

👉 Point to lw

> “The lw instruction reads data from memory during the MEM stage.”

---

👉 Point to add

> “The add instruction needs this data in its EX stage.”

---

## 🔥 IMPORTANT LINE

> “But the data is only available at the end of the MEM stage of lw.”

---

👉 Point to bubble

> “So when add reaches the EX stage, the data is not ready.”

---

## 💬 SAY:

> “Forwarding cannot be used here because the data is not yet available.”

---

👉 Point to stall

> “So the pipeline inserts a stall between ID and EX stages.”

---

## ✅ FINAL LINE

> “This causes a one-cycle delay called a pipeline stall.”


# **1. Pipeline Stalling**

## ✅ **Definition**

**Stalling** is a technique used in pipelining where the processor **pauses the execution of instructions for one or more cycles** until the required data becomes available.

---

## ⚙️ **Why it is needed**

- When an instruction needs data that is **not yet available**
- Mostly happens in **load-use hazard**

---

## 📌 **Where it happens (IMPORTANT)**

- Stall is inserted between **ID → EX stage**



## 🎬 What happens

- A **bubble (empty cycle)** is inserted
- Next instruction is delayed

---

## 🎯 **Effect**

- Increases clock cycles
- Reduces performance

---

# ⚡ 3. CONTROL HAZARD (FLUSHING)

## 💻 Code:

```
addi x1, x0, 5  
addi x2, x0, 5  
beq x1, x2, target  
addi x3, x0, 1  
addi x4, x0, 2  
target:  
addi x5, x0, 9
```

---

## 🎬 Step execution

👉 Point to beq

> “The branch instruction is evaluated in the EX stage.”

---

## 🔥 KEY LINE

> “But the processor fetches the next instruction in the IF stage before knowing the branch result.”

---

👉 Point to wrong instructions

> “So instructions like addi x3 and addi x4 are fetched and move through IF and ID stages.”

---

👉 Then show flush

> “Once the branch decision is made in the EX stage, these incorrect instructions are flushed.”

---

## 💬 SAY:

> “So instructions in IF and ID stages are discarded.”

---

## ✅ FINAL LINE

> “This is called pipeline flushing and it causes performance loss.”



# 🧠 **2. Pipeline Flushing**

## ✅ **Definition**

**Flushing** is a technique where the processor **removes incorrect instructions from the pipeline** when a branch decision changes the flow of execution.

---

## ⚙️ **Why it is needed**

- Happens in **control hazards**
- When branch decision is known late


## What happens

- Incorrect instructions are **discarded**
- Pipeline is cleared partially

---

## 🎯 **Effect**

- Wastes clock cycles
- Reduces efficiency