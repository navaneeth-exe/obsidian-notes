Module: [[DBMS Module 3]]  
Subject: [[Database Management Systems]]  
Semester: [[Semester 4]]
### Definition

**Anomalies** are **problems or inconsistencies that occur in a database when data is redundant or poorly structured**.

They usually happen when the database **is not properly normalized**.

In simple terms:  
Anomalies cause **errors while inserting, updating, or deleting data**.

---

# Types of Anomalies

## 1. Insertion Anomaly

### Definition

An **insertion anomaly** occurs when **we cannot insert data into the database without inserting some other unnecessary data**.

### Example

|Student_ID|Student_Name|Course|
|---|---|---|
|101|Rahul|DBMS|
|102|Anu|OS|

Problem:  
Suppose we want to add a **new course "AI"**, but no student has enrolled yet.

We **cannot insert the course alone** because the table requires **Student_ID and Student_Name**.

⚠️ So we cannot store the course information.

---

## 2. Update Anomaly

### Definition

An **update anomaly** occurs when **updating data in one place requires updating it in multiple places**.

If one place is missed, it leads to **inconsistent data**.

### Example

|Student_ID|Student_Name|Course|
|---|---|---|
|101|Rahul|DBMS|
|101|Rahul|OS|

If Rahul changes his name to **Rahul Kumar**, we must update it in **all rows**.

If we update only one row:

|Student_ID|Student_Name|Course|
|---|---|---|
|101|Rahul Kumar|DBMS|
|101|Rahul|OS|

Now the database becomes **inconsistent**.

---

## 3. Deletion Anomaly

### Definition

A **deletion anomaly** occurs when **deleting some data unintentionally removes other important data**.

### Example

|Student_ID|Student_Name|Course|
|---|---|---|
|101|Rahul|DBMS|
|102|Anu|OS|

If we delete the record:

```
102 | Anu | OS
```

We also **lose the information that course "OS" exists**.

⚠️ Important data gets deleted accidentally.

---

