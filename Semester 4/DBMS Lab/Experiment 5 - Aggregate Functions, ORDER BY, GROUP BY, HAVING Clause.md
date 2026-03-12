# 1️⃣ Aim of the Experiment

To understand and implement **SQL aggregate functions** and clauses such as **ORDER BY, GROUP BY, and HAVING** to perform calculations and organize query results.

These are used to **summarize and analyze data in tables**.

---

# 2️⃣ Concepts Used

This experiment demonstrates:

- Aggregate functions
    
- Sorting data
    
- Grouping records
    
- Filtering grouped results
    

Important SQL operations used:

|Feature|Purpose|
|---|---|
|Aggregate Functions|Perform calculations on data|
|ORDER BY|Sort query results|
|GROUP BY|Group rows with similar values|
|HAVING|Filter grouped results|

---

# 3️⃣ SQL Code Explanation

---

# Step 1: Create Database

```
CREATE DATABASE studentdb;  
USE studentdb;
```

Explanation:

`CREATE DATABASE studentdb`

Creates a new database named **studentdb**.

`USE studentdb`

Selects this database for performing operations.

---

# Step 2: Create Student Table

```
CREATE TABLE Student (  
student_id INT PRIMARY KEY,  
name VARCHAR(50),  
department VARCHAR(50),  
marks INT  
);

```
Explanation:

|Column|Meaning|
|---|---|
|student_id|Unique ID of student|
|name|Student name|
|department|Student department|
|marks|Marks obtained|

`PRIMARY KEY`

Ensures each student has a **unique ID**.

---

# Step 3: Insert Data

```
INSERT INTO Student VALUES  
(1, 'Amit', 'CSE', 85),  
(2, 'Ravi', 'ECE', 78),  
(3, 'Neha', 'CSE', 92),  
(4, 'Priya', 'EEE', 65),  
(5, 'Rahul', 'ECE', 88),  
(6, 'Anu', 'CSE', 70);
```

Explanation:

Six student records are inserted.

Example table:

|ID|Name|Dept|Marks|
|---|---|---|---|
|1|Amit|CSE|85|
|2|Ravi|ECE|78|
|3|Neha|CSE|92|
|4|Priya|EEE|65|
|5|Rahul|ECE|88|
|6|Anu|CSE|70|

---

# 4️⃣ Aggregate Functions

Aggregate functions perform **calculations on multiple rows** and return a **single value**.

---

# COUNT Function

```
SELECT COUNT(*) AS total_students FROM Student;
```

Explanation:

`COUNT(*)`

Counts total number of rows in table.

Output:

|total_students|
|---|
|6|

---

# SUM Function

```
SELECT SUM(marks) AS total_marks FROM Student;
```

Explanation:

Adds marks of all students.

Calculation:

85 + 78 + 92 + 65 + 88 + 70 = **478**

Output:

|total_marks|
|---|
|478|

---

# AVG Function

```
SELECT AVG(marks) AS average_marks FROM Student;
```

Explanation:

Calculates average marks.

Formula:

SUM(marks) / number_of_students

478 / 6 = **79.67**

---

# MAX Function

```
SELECT MAX(marks) AS highest_marks FROM Student;
```

Explanation:

Returns highest marks.

Output:

|highest_marks|
|---|
|92|

---

# MIN Function

```
SELECT MIN(marks) AS lowest_marks FROM Student;
```

Explanation:

Returns lowest marks.

Output:

|lowest_marks|
|---|
|65|

---

# 5️⃣ ORDER BY Clause

Used to **sort query results**.

---

### Ascending Order

```
SELECT name, marks  
FROM Student  
ORDER BY marks ASC;
```

Explanation:

Sorts students by **marks in ascending order**.

Output example:

|Name|Marks|
|---|---|
|Priya|65|
|Anu|70|
|Ravi|78|
|Amit|85|
|Rahul|88|
|Neha|92|

---

### Descending Order

SELECT name, department  
FROM Student  
ORDER BY name DESC;

Explanation:

Sorts student names **in reverse alphabetical order**.

Example output:

|Name|
|---|
|Ravi|
|Rahul|
|Priya|
|Neha|
|Anu|
|Amit|

---

# 6️⃣ GROUP BY Clause

Used to **group rows having the same values**.

---

Example:

SELECT department, COUNT(student_id) AS total_students  
FROM Student  
GROUP BY department;

Explanation:

Counts number of students in each department.

Output:

|Department|Students|
|---|---|
|CSE|3|
|ECE|2|
|EEE|1|

---

# Average Marks per Department

SELECT department, AVG(marks) AS average_marks  
FROM Student  
GROUP BY department;

Explanation:

Calculates **average marks per department**.

Example output:

|Department|Avg Marks|
|---|---|
|CSE|82.3|
|ECE|83|
|EEE|65|

---

# 7️⃣ HAVING Clause

HAVING filters **grouped results**.

It is similar to WHERE but used **after GROUP BY**.

---

### Example

SELECT department, COUNT(student_id) AS total_students  
FROM Student  
GROUP BY department  
HAVING COUNT(student_id) > 2;

Explanation:

Displays departments with **more than 2 students**.

Output:

|Department|Students|
|---|---|
|CSE|3|

---

### Another Example

SELECT department, AVG(marks) AS average_marks  
FROM Student  
GROUP BY department  
HAVING AVG(marks) > 80;

Output:

|Department|Avg Marks|
|---|---|
|CSE||
|ECE||

Departments with average marks **above 80**.

---

# 8️⃣ Result

The aggregate functions and SQL clauses were successfully used to **analyze and organize student data**.

---

# 9️⃣ Possible Viva Questions (With Answers)

---

### Q1. What are aggregate functions?

**Answer**

Aggregate functions perform calculations on multiple rows and return a single result.

Examples:

- COUNT
    
- SUM
    
- AVG
    
- MAX
    
- MIN
    

---

### Q2. What does COUNT(*) do?

**Answer**

COUNT(*) returns the total number of rows in a table.

---

### Q3. What is the difference between SUM and AVG?

**Answer**

SUM calculates the total value, while AVG calculates the average value.

---

### Q4. What is ORDER BY clause?

**Answer**

ORDER BY is used to sort query results in ascending or descending order.

---

### Q5. What is GROUP BY?

**Answer**

GROUP BY groups rows that have the same values in specified columns.

---

### Q6. Why is GROUP BY used with aggregate functions?

**Answer**

It allows calculations like COUNT or AVG to be performed separately for each group.

---

### Q7. What is HAVING clause?

**Answer**

HAVING filters grouped results after GROUP BY.

---

### Q8. Difference between WHERE and HAVING?

|WHERE|HAVING|
|---|---|
|Filters rows|Filters groups|
|Used before grouping|Used after GROUP BY|

---

### Q9. Can HAVING be used without GROUP BY?

**Answer**

Yes, but it is usually used with GROUP BY.

---

### Q10. What is default sorting order in ORDER BY?

**Answer**

Ascending order (ASC).

---

# 🔟 Tricky Viva Questions (Teachers Love These)

---

### Q: Why can't we use WHERE with aggregate functions?

Answer:

Because WHERE filters rows before grouping, while aggregate functions operate on grouped data.

---

### Q: Which executes first, WHERE or GROUP BY?

Answer:

Execution order:

1. FROM
    
2. WHERE
    
3. GROUP BY
    
4. HAVING
    
5. SELECT
    
6. ORDER BY
    

---

### Q: Can ORDER BY be used with GROUP BY?

Answer:

Yes, ORDER BY can sort grouped results.