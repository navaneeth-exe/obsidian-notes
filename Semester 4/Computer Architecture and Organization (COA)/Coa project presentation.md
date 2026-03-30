

# 🎤 🔥 FINAL PRESENTATION (WITH STAGE NAMES)

---

# 🟢 TRANSITION

> “Now I will demonstrate pipeline hazards and how they are handled in a 5-stage pipelined RISC-V processor.”

---

## 💥 ALSO SAY THIS ONCE

> “The five stages are: Instruction Fetch (IF), Instruction Decode (ID), Execute (EX), Memory Access (MEM), and Write Back (WB).”

---

# ⚡ 1. DATA HAZARD (FORWARDING)

## 💻 Code:

```c
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

---

# ⚡ 2. LOAD-USE HAZARD (STALL)

## 💻 Code:

```c
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

---

# ⚡ 3. CONTROL HAZARD (FLUSHING)

## 💻 Code:

```c
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

---

# 🟡 PAGE 10 — RESULTS (WITH STAGES)

---

## 💬 SAY:

> “Each instruction passes through IF, ID, EX, MEM, and WB stages.”

---

👉 Show pipeline

> “Different instructions occupy different stages at the same time.”

---

## 🔥 IMPORTANT LINE

> “This overlapping of stages improves throughput.”

---

## 👉 CONNECT HAZARDS

> “In data hazard, forwarding occurs between MEM and EX stages.”

> “In load-use hazard, a stall is inserted between ID and EX stages.”

> “In control hazard, instructions in IF and ID stages are flushed.”

---

# 🟣 PAGE 11 — ANALYSIS (PRO LEVEL)

---

## 💬 SAY:

> “Pipeline improves performance by executing multiple instructions across IF, ID, EX, MEM, and WB stages simultaneously.”

---

> “Data hazards are resolved using forwarding between stages.”

---

> “Load-use hazards cause delay because data is only available after MEM stage.”

---

> “Control hazards cause flushing of instructions in IF and ID stages.”

---

## 🔥 FINAL LINE

> “So although pipelining improves throughput, hazards increase clock cycles and reduce efficiency.”

---

# 💻 DATAPATH EXPLANATION (STAGE-WISE)

👉 Open datapath

---

## 💬 SAY:

> “In IF stage, instruction is fetched from instruction memory.”

> “In ID stage, registers are read.”

> “In EX stage, ALU performs computation.”

> “In MEM stage, data memory is accessed.”

> “In WB stage, result is written back to register.”

---

## 🔥 FINAL LINE

> “All these stages operate simultaneously for different instructions.”

---

# 🧠 FINAL CHEAT CODE

If you forget everything, just say:

👉 “In EX stage…”  
👉 “In MEM stage…”  
👉 “Between ID and EX…”

💀 That alone will boost your marks.

---

If you want next: 🔥 I can simulate **full viva grilling with answers**  
🔥 Or give you **diagram-based explanation like your PDF (cycle-wise)** which examiners LOVE