Module: [[COA Module 3]]

# 1. Spatial Locality

## Definition

**Spatial locality** means that if a memory location is accessed, nearby memory locations are likely to be accessed soon.

👉 Programs tend to access data that is physically close to recently accessed data.

---

## Why It Happens

- Arrays are stored in contiguous memory.
- Instructions are stored sequentially.
- Loop variables are accessed consecutively.

---

## Example

```
`for(int i = 0; i < 10; i++) {`  
	`sum += arr[i];`  
`}`
```

If `arr[0]` is accessed, then `arr[1]`, `arr[2]`, `arr[3]`… will also be accessed.

Since these elements are stored next to each other in memory → spatial locality exists.

---

## In Cache

When one memory block is loaded into cache:
- Neighboring memory addresses are also loaded.
- This improves cache hit rate.