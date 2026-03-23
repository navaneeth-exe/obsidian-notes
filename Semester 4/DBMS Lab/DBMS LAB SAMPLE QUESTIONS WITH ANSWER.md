

---





### **Question:**

![[Pasted image 20260323234516.png]]
Create Employee and Department tables with given constraints.

### **Answer:**

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

---

# 🧠 **QUERIES**

---

## **1. Employees earning more than average salary**

**Question:**  
Display all employees who earn more than the average salary.

**Answer:**

SELECT *  
FROM Employee  
WHERE Salary > (SELECT AVG(Salary) FROM Employee);

👉 Uses **subquery + aggregate (AVG)**

---

## **2. Display Eid, Ename and Dname**

**Question:**  
Display Eid, Ename and Dname.

**Answer:**

SELECT E.Eid, E.Ename, D.Dname  
FROM Employee E  
JOIN Department D  
ON E.DeptId = D.DeptId;

👉 Uses **JOIN to combine tables**

---

## **3. Sort employees by salary (descending)**

**Question:**  
Sort the employee table in descending order of salaries.

**Answer:**

SELECT *  
FROM Employee  
ORDER BY Salary DESC;

👉 `DESC = high → low`

---

## **4. List job designations without repetition**

**Question:**  
List all job designations without repetition.

**Answer:**

SELECT DISTINCT Designation  
FROM Employee;

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