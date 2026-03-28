## 🎯 **AIM**

To implement the **Shortest Seek Time First (SSTF)** disk scheduling algorithm and calculate total head movement.

---

## 📚 **THEORY**

SSTF (Shortest Seek Time First) selects the disk request that is **closest to the current head position**.

- It reduces total seek time
- Improves performance compared to FCFS
- But may cause **starvation** for far requests

👉 Idea:

> Always move the disk head to the nearest request next.

---

# 🧾 **ALGORITHM**

**Step 1:** Start

**Step 2:** Read initial head position

**Step 3:** Generate or input disk requests

**Step 4:** Initialize:

- `visited[]` array = 0
- `total = 0`
- `current = head`

**Step 5:** Repeat until all requests are served

- Find nearest unvisited request
- Calculate distance = |current – request|
- Add distance to total
- Mark request as visited
- Move head to that request

**Step 6:** Print total head movement

**Step 7:** Stop