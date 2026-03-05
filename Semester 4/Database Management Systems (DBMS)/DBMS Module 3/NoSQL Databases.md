### Definition

**NoSQL (Not Only SQL)** databases are **non-relational databases** designed to store and manage **large volumes of unstructured or semi-structured data**.

Unlike traditional relational databases, NoSQL databases **do not use fixed table schemas** and are designed for **high scalability and distributed systems**.

---

# Types of NoSQL Databases

## 1. Document-Based Database

### Description

Data is stored in **documents**, usually in formats like **JSON or BSON**.
Each document contains **key–value pairs** and can have different structures.
### Example

```
{  
  "student_id": 101,  
  "name": "Rahul",  
  "course": "DBMS"  
}
```
### Examples of Databases

- MongoDB
- CouchDB
### Best Use Case

- Content management systems
- Web applications
- Semi-structured data

---

## 2. Key–Value Store

### Description

Data is stored as **key-value pairs** where a **key is used to access its value**.
This is the **simplest type of NoSQL database**.

### Example

```
Key: User123  
Value: Rahul
```
### Examples of Databases

- Redis
- DynamoDB

### Best Use Case

- Caching
- Session management
- Fast data retrieval


---

## 3. Column-Oriented Database

### Description

Data is stored in **columns instead of rows**.
This structure is useful for **large-scale data analysis and big data processing**.

### Examples of Databases

- Cassandra
- HBase

### Best Use Case

- Big data analytics
- Data warehouses

---

## 4. Graph Database

### Description

Data is stored as **nodes and relationships**.
Nodes represent **entities**, and edges represent **relationships between them**.

### Examples of Databases

- Neo4j
- Amazon Neptune
### Best Use Case

- Social networks
- Recommendation systems
- Network analysis

---

# Uses of NoSQL Databases

NoSQL databases are used for:

1. **Handling large volumes of data**
2. **Big data and real-time web applications**
3. **Distributed systems**
4. **Social media platforms**
5. **Content management systems**
6. **IoT and real-time analytics**

Example applications:
- Faceboo
- Instagram
- Amazon

---

# Limitations of NoSQL

1. **Limited support for complex queries**
2. **Lack of standard query language like SQL**
3. **Data consistency may be weaker (eventual consistency)**
4. **Less support for transactions compared to relational databases**
5. **Data duplication may occur**


---

Module : [[DBMS Module 3]]