## **Given**

- Cache size = **16 bytes**
- Block size = **4 bytes**
- Mapping = **2-way set associative**

---

![[Pasted image 20260414020051.png]]


---

## **Final Address Format**

```
| Tag | Set Index (1 bit) | Offset (2 bits) |
```

---

## **Step 4: Mapping Formula**

$$
	Set Number=Block Number(mod)  2
$$

---

## **Step 5: Example Mapping**

Take memory blocks:  
**0, 1, 2, 3, 4, 5**

|Block Number|Set (mod 2)|
|---|---|
|0|0|
|1|1|
|2|0|
|3|1|
|4|0|
|5|1|

---

## **Step 6: Cache Placement**

Each set has **2 blocks (2-way)**

- **Set 0** → blocks 0, 2 (next → replace using LRU)
- **Set 1** → blocks 1, 3 (next → replace using LRU)

---

## **Key Points (Write this 💯)**

- Total blocks = **4**
- Sets = **2**
- Offset = **2 bits**
- Set index = **1 bit**
- Replacement needed when set is full

---

## **Important Line 😏**

2-way associative allows **2 blocks per set**, reducing conflicts compared to direct mapping.