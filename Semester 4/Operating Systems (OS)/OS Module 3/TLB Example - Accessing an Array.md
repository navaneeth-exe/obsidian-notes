## **Given**

- Array size = **10 elements**
- Each element = **4 bytes**
- Starting Virtual Address = **100**
- Virtual Address Space = **8-bit (256 bytes)**
- Page size = **16 bytes**

---

## **Address Format**

👉 VA = 8 bits → split into:

```
VA = [ VPN (4 bits) | Offset (4 bits) ]
```

- Offset = 4 bits → page size = 16 bytes
- VPN = 4 bits → total pages = 16

---

## **Memory Layout Understanding**

👉 Each page holds:
```
16 bytes / 4 bytes = 4 elements per page
```
So:

- Page 6 → a[0], a[1], a[2], a[3]
- Page 7 → a[4], a[5], a[6], a[7]
- Page 8 → a[8], a[9]

---

## **Step-by-Step Execution**

We run:

```
for(i=0; i<10; i++)  
    sum += a[i];
```

---

## **Access Pattern + TLB Behavior**

### 🔴 Access a[0]

- VA = 100
- VPN = 6
- First time → **TLB Miss** ❌
- Load mapping into TLB

---

### 🟢 Access a[1]

- Same page (VPN = 6)  
    👉 **TLB Hit** ✅

---

### 🟢 Access a[2]

👉 Same page → **Hit** ✅

---

### 🟢 Access a[3]

👉 Same page → **Hit** ✅

---

### 🔴 Access a[4]

- New page (VPN = 7)  
    👉 **TLB Miss** ❌
- Add new entry

---

### 🟢 Access a[5]

👉 Same page → **Hit** ✅

---

### 🟢 Access a[6]

👉 Same page → **Hit** ✅

---

### 🟢 Access a[7]

👉 Same page → **Hit** ✅

---

### 🔴 Access a[8]

- New page (VPN = 8)  
    👉 **TLB Miss** ❌

---

### 🟢 Access a[9]

👉 Same page → **Hit** ✅

---

## **Final Result (VERY IMPORTANT)**

👉 From your PDF:

- **TLB Misses = 3**
- **TLB Hits = 7**

---

## **Visualization of Hits & Misses**

👉 Pattern:

```
Index:   0 1 2 3 4 5 6 7 8 9  
Result:  M H H H M H H H M H
```
---

## **Key Insight (EXAM GOLD)**

💡 Why hits happen:

- **Spatial locality**
- Consecutive elements are in **same page**

---

## **Important Observations**

- First access to a page → **Miss**
- Remaining accesses in same page → **Hits**
- Number of misses = number of **distinct pages accessed**