### Definition

**Normalization** is the process of **organizing data in a database to reduce redundancy (duplicate data) and eliminate [[Anomalies]]** by dividing large tables into smaller related tables.

In simple terms:  
Normalization helps to **store data efficiently and avoid data repetition**.

---
## Why Normalization is Needed

Normalization helps to:

- **Remove duplicate data**
- **Improve data consistency**
- **Reduce storage space**
- **Avoid [[Anomalies]] (insert, update, delete problems)**
- **Maintain data integrity**

---

## Example (Without Normalization)

Student Table

|Student_ID|Student_Name|Course|Instructor|
|---|---|---|---|
|101|Rahul|DBMS|Anil|
|101|Rahul|OS|Meera|
|102|Anu|DBMS|Anil|

Problems:

- **Student name repeats**
- **Instructor repeats**
- Waste of storage
- Hard to update

---

## After Normalization

### Student Table

|Student_ID|Student_Name|
|---|---|
|101|Rahul|
|102|Anu|

### Course Table

|Course|Instructor|
|---|---|
|DBMS|Anil|
|OS|Meera|

### Enrollment Table

|Student_ID|Course|
|---|---|
|101|DBMS|
|101|OS|
|102|DBMS|

Now:

- No duplication
- Data stored efficiently