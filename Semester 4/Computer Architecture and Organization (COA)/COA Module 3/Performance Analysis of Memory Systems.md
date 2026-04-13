## **Definition**

The performance of a memory system is evaluated using parameters such as **hit rate, miss rate, access time, memory cycle time, bandwidth, and AMAT**.

---

## **1. Hit and Miss**

- **Cache Hit** → Data found in cache (fast access)
- **Cache Miss** → Data not found, fetched from lower memory (slow)

---

## **2. Hit Rate (H)**

Hit Rate=Number of HitsTotal Memory Accesses\text{Hit Rate} = \frac{\text{Number of Hits}}{\text{Total Memory Accesses}}Hit Rate=Total Memory AccessesNumber of Hits​

- Higher hit rate → better performance

---

## **3. Miss Rate (MR)**

Miss Rate=1−Hit Rate\text{Miss Rate} = 1 - \text{Hit Rate}Miss Rate=1−Hit Rate

---

## **4. Access Time**

- Time taken to **read or write data from memory**
- Lower access time → faster memory

---

## **5. Memory Cycle Time**

- Total time required to **complete one memory operation**
- Includes access time + recovery time
- Usually **greater than access time**

---

## **6. Bandwidth**

- Amount of data transferred **per unit time**
- Measured in **bytes/sec**
- Higher bandwidth → better performance

---

## **7. Average Memory Access Time (AMAT)**

AMAT=Hit Time+(Miss Rate×Miss Penalty)\text{AMAT} = \text{Hit Time} + (\text{Miss Rate} \times \text{Miss Penalty})AMAT=Hit Time+(Miss Rate×Miss Penalty)

- Represents **average time to access memory**
- Includes both hit and miss cases

---

## **Key Points (Write this 💯)**

- Performance depends on:
    - Hit rate
    - Miss rate
    - Access time
    - Memory cycle time
    - Bandwidth
    - AMAT
- Lower access time & AMAT → better system
- Higher bandwidth & hit rate → better performance

---

## **Important Line 😏**

Memory performance improves when **hit rate increases, access time decreases, and bandwidth increases**.