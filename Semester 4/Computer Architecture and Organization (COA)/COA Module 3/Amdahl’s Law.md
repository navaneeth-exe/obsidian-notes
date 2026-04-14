**Definition**

Amdahl’s Law states that the **overall speedup of a system depends on the fraction of execution time that can be improved**.

Even if one part of a system is made very fast, the **overall performance improvement is limited by the part that is not improved**.

---

## Formula

$$
Speedup = \frac{1}{(1-f) + \frac{f}{S}}​
$$

Where:

- **f** = Fraction of execution time affected by the improvement
- **S** = Speedup of the improved portion
- **(1 − f)** = Fraction of execution time **not improved**

---

## Example

Suppose:

- **50% of the program is memory operations**
- Memory is made **10 times faster**

So,

```
f=0.5 
S=10
```
---

![[Pasted image 20260415011355.png|659]]
---

## Final Answer

**Overall Speedup ≈ 1.82**

This shows that even though memory is **10× faster**, the **overall system improves only about 1.82×** because the remaining part of the program is not improved.

---

## Small concluding line (teachers like this)

Thus, **Amdahl’s Law shows that system performance improvement is limited by the portion of the system that cannot be improved.**