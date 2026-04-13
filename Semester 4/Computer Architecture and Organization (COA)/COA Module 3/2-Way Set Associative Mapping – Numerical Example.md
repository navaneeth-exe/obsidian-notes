## **Given**

- Cache size = **16 bytes**
- Block size = **4 bytes**
- Mapping = **2-way set associative**

---

## **Step 1: Number of cache blocks**

$$
Blocks=164=4 blocks\text{Blocks} = \frac{16}{4} = 4 \text{ blocks}Blocks=416​=4 blocks
$$

---

## **Step 2: Number of sets**

Sets=42=2 sets\text{Sets} = \frac{4}{2} = 2 \text{ sets}Sets=24​=2 sets

---

## **Step 3: Address Format**

Assume memory is byte addressable.

### **Block offset bits**

log⁡2(4)=2 bits\log_2(4) = 2 \text{ bits}log2​(4)=2 bits

---

### **Set index bits**

log⁡2(2)=1 bit\log_2(2) = 1 \text{ bit}log2​(2)=1 bit

---

### **Tag bits**

Remaining bits=Tag\text{Remaining bits} = \text{Tag}Remaining bits=Tag

---

## **Final Address Format**

| Tag | Set Index (1 bit) | Offset (2 bits) |

---

## **Step 4: Mapping Formula**

Set Number=Block Numbermod  2\text{Set Number} = \text{Block Number} \mod 2Set Number=Block Numbermod2

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