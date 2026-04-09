## ✅ **Answer (Write this in exam)**

Concurrency control is required in a database system to ensure that **simultaneous execution of multiple transactions does not lead to data inconsistency**.

When transactions execute concurrently without control, they may interfere with each other and produce **incorrect or inconsistent results**.

---

## 🔥 **Reasons Why Concurrency Control is Needed**

---

### 1️⃣ **To Maintain Data Consistency**

👉 Ensures database remains in a **correct and valid state**

- Prevents incorrect updates
- Maintains integrity of data

---

### 2️⃣ **To Prevent Concurrency Problems**

👉 Avoids issues like:

- Lost update
- Dirty read
- Unrepeatable read
- Incorrect summary

---

### 3️⃣ **To Ensure Isolation (ACID Property)**

👉 Each transaction executes as if it is **alone in the system**

- No interference from other transactions

---

### 4️⃣ **To Achieve Serializability**

👉 Ensures that concurrent execution gives **same result as serial execution**

- Maintains correctness with concurrency

---

### 5️⃣ **To Improve System Performance Safely**

👉 Allows parallel execution **without errors**

- Combines speed + correctness