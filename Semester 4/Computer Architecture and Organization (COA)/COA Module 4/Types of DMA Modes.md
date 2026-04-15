**Direct Memory Access (DMA)** allows data transfer between I/O devices and memory without continuous CPU intervention.

The main DMA modes are:

---

## 🔹 1. Burst Mode (Block Transfer Mode)

- DMA transfers the **entire block of data at once**.
- It **takes full control of the system bus**.
- CPU operation is **completely suspended** during transfer.

**Advantages:**

- High-speed data transfer
- Efficient for large data blocks

**Disadvantage:**

- CPU remains idle during transfer

---

## 🔹 2. Cycle Stealing Mode

- DMA transfers data **one word at a time**.
- It **temporarily steals bus cycles** from the CPU.
- CPU is paused briefly, then resumes execution.

**Advantages:**

- CPU is not completely halted
- Better system utilization

**Disadvantage:**

- Slight slowdown of CPU

---

## 🔹 3. Transparent Mode (Hidden Mode)

- DMA transfers data **only when CPU is idle**.
- It does not interfere with CPU operation.

**Advantages:**

- No effect on CPU performance

**Disadvantage:**

- Slowest mode of transfer