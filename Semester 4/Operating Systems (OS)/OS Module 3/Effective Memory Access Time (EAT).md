# **1. EAT with TLB**

## **Concept**

- TLB speeds up address translation
- Two cases:
    - **TLB Hit** → fast
    - **TLB Miss** → slow

---

## **Formula**

Let:

- Hit ratio = **h**
- Memory access time = **m**

👉 Then:

$$
EAT=h×(m)+(1−h)×(2m)
$$

👉 Simplified:

$$
EAT=(2−h)×m
$$

EMAT = h(t+m) + (1 – h)(t+2m)


---

## **Explanation**

- Hit → 1 memory access
- Miss → 2 memory accesses (page table + data)

---

## **Example**

If:

- h = 0.9
- m = 100 ns

			EAT=0.9×100+0.1×200=110 ns

👉 Faster than 200 ns 😎

---

# **2. EAT with Page Fault**

## **Concept**

- Page fault is very costly (disk access)
- Happens rarely but affects performance heavily

---

## **Formula**

Let:

- Page fault rate = **p**
- Memory access time = **m**
- Page fault service time = **F**

👉 Then:

$$
EAT=(1−p)×m+p×F
$$

---

## **Explanation**

- No fault → normal memory access
- Fault → huge delay (disk I/O + OS handling)

---

## **Expanded Fault Time (IMPORTANT)**

Page fault service time includes:

- Trap to OS
- Disk access
- Swap in page
- Update page table
- Restart instruction

👉 So:

$$
F≫m
$$

---

## **Example**

If:

- m = 100 ns
- p = 0.001
- F = 8 ms = 8,000,000 ns

EAT=(1−0.001)×100+0.001×8,000,000
=99.9+8000=8099.9 ns
👉 HUGE increase 😬