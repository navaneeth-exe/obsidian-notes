# 2. Temporal Locality 

## Definition

**Temporal locality** means that if a memory location is accessed, it is likely to be accessed again in the near future.

👉 Recently used data will probably be used again soon.

---

## Why It Happens

- Variables inside loops are reused.
- Frequently called functions.
- Repeated condition checks.

---

## Example

```
for(int i = 0; i < 100; i++) {  
	count++;  
}
```
The variable `count` is accessed repeatedly.

Since it is used again and again within a short time → temporal locality exists.

---

## In Cache

Recently accessed data is kept in cache because:
- It has high probability of reuse.
- Reduces memory access time.