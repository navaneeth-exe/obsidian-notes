
![[Pasted image 20260323234547.png]]
---

## **1. Create Supplier Table**

**Question:**  
Create a Supplier table as shown.

**Answer:**

```
CREATE TABLE Supplier (  
    Sup_No VARCHAR(5) PRIMARY KEY,  
    Sup_Name VARCHAR(50),  
    Item_Supplied VARCHAR(50),  
    Item_Price INT,  
    City VARCHAR(50)  
);
```
---

## **2. Supplier numbers & names starting with 'R'**

**Question:**  
Display supplier numbers and names whose name starts with 'R'.

**Answer:**
```
SELECT Sup_No, Sup_Name  
FROM Supplier  
WHERE Sup_Name LIKE 'R%';
```

---

## **3. Suppliers supplying Processor in Delhi**

**Question:**  
Display names of suppliers who supply Processor and are in Delhi.

**Answer:**

```
SELECT Sup_Name  
FROM Supplier  
WHERE Item_Supplied = 'Processor' AND City = 'Delhi';
```

---

## **4. Suppliers supplying same items as Ramesh**

**Question:**  
Display names of suppliers who supply same items as Ramesh.

**Answer:**

```
SELECT Sup_Name  
FROM Supplier  
WHERE Item_Supplied = (  
    SELECT Item_Supplied  
    FROM Supplier  
    WHERE Sup_Name = 'Ramesh'  
);
```

---

## **5. Increase price of Keyboard by 200**

**Question:**  
Increase the price of Keyboard by 200.

**Answer:**

```
UPDATE Supplier  
SET Item_Price = Item_Price + 200  
WHERE Item_Supplied = 'Keyboard';
```

---

## **6. Suppliers in Delhi sorted by price**

**Question:**  
Display supplier number, name, and item price for suppliers in Delhi in ascending order.

**Answer:**

```
SELECT Sup_No, Sup_Name, Item_Price  
FROM Supplier  
WHERE City = 'Delhi'  
ORDER BY Item_Price ASC;
```

---

## **7. Add new column CONTACTNO**

**Question:**  
Add a new column CONTACTNO.

**Answer:**

```
ALTER TABLE Supplier  
ADD CONTACTNO VARCHAR(15);
```

---

### ⚠️ Small brain-boost (exam trap alert)

- `LIKE 'R%'` → starts with R
- Subquery in Q4 is **very important**, they love asking that
- `UPDATE price = price + 200` → don’t write fixed value ❌

---





### 2.  **Question:**

![[Pasted image 20260323234516.png]]
Create Employee and Department tables with given constraints.

### **Answer:**

```
CREATE TABLE Department (  
    DeptId VARCHAR(5) PRIMARY KEY,  
    Dname VARCHAR(50) NOT NULL  
);

CREATE TABLE Employee (  
    Eid INT PRIMARY KEY,  
    Ename VARCHAR(50),  
    DeptId VARCHAR(5),  
    Designation VARCHAR(50),  
    Salary INT CHECK (Salary >= 10000),  
    DOJ DATE,  
    FOREIGN KEY (DeptId) REFERENCES Department(DeptId)  
);
```

---

# 🧠 **QUERIES**

---

## **1. Employees earning more than average salary**

**Question:**  
Display all employees who earn more than the average salary.

**Answer:**

```
SELECT *  
FROM Employee  
WHERE Salary > (SELECT AVG(Salary) FROM Employee);
```

👉 Uses **subquery + aggregate (AVG)**

---

## **2. Display Eid, Ename and Dname**

**Question:**  
Display Eid, Ename and Dname.

**Answer:**

```
SELECT E.Eid, E.Ename, D.Dname  
FROM Employee E  
JOIN Department D  
ON E.DeptId = D.DeptId;
```
👉 Uses **JOIN to combine tables**

---

## **3. Sort employees by salary (descending)**

**Question:**  
Sort the employee table in descending order of salaries.

**Answer:**

```
SELECT *  
FROM Employee  
ORDER BY Salary DESC;
```

👉 `DESC = high → low`

---

## **4. List job designations without repetition**

**Question:**  
List all job designations without repetition.

**Answer:**

```
SELECT DISTINCT Designation  
FROM Employee;
```

👉 `DISTINCT removes duplicates`

---

## **5. Department-wise employees sorted by salary**

**Question:**  
Display employee details department-wise in ascending order of salary.

**Answer:**

SELECT *  
FROM Employee  
ORDER BY DeptId, Salary ASC;

👉 First Dept → then Salary inside it

---

## **6. Clerks in Dept D2**

**Question:**  
Display all clerks in DeptId D2.

**Answer:**

SELECT *  
FROM Employee  
WHERE Designation = 'Clerk' AND DeptId = 'D2';

👉 Uses `AND` condition

---

## **7. Employees joined in 2011**

**Question:**  
Display employees who joined in the year 2011.

**Answer:**

SELECT *  
FROM Employee  
WHERE YEAR(DOJ) = 2011;

👉 Extract year from date

---

# ⚠️ Quick Memory Hacks (last-minute save)

- Subquery → Q1
- JOIN → Q2
- DESC → Q3
- DISTINCT → Q4
- ORDER BY multiple → Q5
- AND condition → Q6
- YEAR() → Q7