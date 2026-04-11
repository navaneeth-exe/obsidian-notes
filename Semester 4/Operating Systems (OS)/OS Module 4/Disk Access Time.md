## **Definition**

**Disk Access Time** is the total time required to **locate and retrieve data from a disk**.---

## **1. Seek Time (Ts)**

- Time taken for the **read/write head to move** to the required track

👉 Depends on distance between tracks

---

## **2. Rotational Latency (Tr)**

- Time taken for the **disk to rotate** so that required sector comes under the head

👉 Average = half rotation

---

## **3. Transfer Time (Tt)**

- Time taken to **read/write the data** once head is in position

---

## **4. Controller Overhead (optional)**

- Time for controller to process request

---

# **Total Disk Access Time Formula**

Disk Access Time=Ts+Tr+Tt\text{Disk Access Time} = T_s + T_r + T_tDisk Access Time=Ts​+Tr​+Tt​