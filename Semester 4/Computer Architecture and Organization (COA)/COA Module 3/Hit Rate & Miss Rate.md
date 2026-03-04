Module: [[COA Module 3]]
## Hit Rate

**Definition:**  
Hit rate is the fraction of memory accesses that are found in the cache.

When the CPU looks for data and it is already present in cache → that’s a **cache hit**.

**Formula:**

$$
Hit\ Rate = \frac{Number\ of\ Cache\ Hits}{Total\ Memory\ Accesses}
$$

**Example:**  
If out of 100 memory accesses, 85 are found in cache:

$$
Hit Rate=85100=0.85=85%\text{Hit Rate} = \frac{85}{100} = 0.85 = 85\%Hit Rate=10085​=0.85=85\%
$$

---

##  Miss Rate

**Definition:**  
Miss rate is the fraction of memory accesses that are **not found** in cache.

When CPU searches cache and data is not there → that’s a **cache miss**.

**Formula:**

$$
{Miss Rate} = \frac{\text{Number of Cache Misses}}{\text{Total Memory Accesses}}​
$$

OR

$$
{Miss Rate} = 1 - \text{Hit Rate}
$$

**Example:**  
If hit rate = 85%
$$
Miss Rate=1−0.85=0.15=15%\text{Miss Rate} = 1 - 0.85 = 0.15 = 15\%Miss Rate=1−0.85=0.15=15%percentage
$$
---

## 🔥 Important Relation
$$

Hit Rate+Miss Rate=1
$$