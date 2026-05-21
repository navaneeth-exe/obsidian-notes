# 1. Vendor Table

|Vendor_ID|Vendor_Name|Product_Supplied|Product_Price|City|
|---|---|---|---|---|
|V1|Ajay|Monitor|7000|Pune|
|V2|Deepak|Keyboard|1200|Chennai|
|V3|Ravi|Printer|8500|Delhi|
|V4|Manoj|Mouse|600|Mumbai|
|V5|Tarun|Keyboard|1500|Bangalore|
|V6|Sandeep|Scanner|5000|Hyderabad|

### Questions

1. Display Vendor IDs and Vendor names whose names start with letter ‘M’.
    
2. Display the names of vendors supplying Keyboard from Chennai.
    
3. Display vendors who supply the same product as Tarun.
    
4. Increase the price of Mouse by 300.
    
5. Display vendor details from Delhi sorted by product price.
    
6. Add a column named EmailId.
    
7. Delete the record having the highest product price.
    
8. Display all products costing more than 5000.
    
9. Count total vendors in the table.
    
10. Display distinct cities from the table.
    

---

# 2. Staff Table

|Staff_ID|Staff_Name|DOB|Designation|Salary|DOJ|
|---|---|---|---|---|---|
|ST101|Anita|12-Feb-90|Developer|45000|10-Jun-15|
|ST102|Rahul|18-Aug-95|Tester|35000|22-Jan-20|
|ST103|Meera|25-Dec-88|HR|40000|11-Jul-14|
|ST104|Vivek|03-Mar-92|Developer|55000|18-Apr-18|
|ST105|Kavya|15-Oct-85|Manager|70000|05-May-12|
|ST106|Rohan|07-Jan-91|Analyst|50000|09-Sep-19|

### Questions

1. Display all Developers.
    
2. Display employees who joined after 2017.
    
3. Display staff names ending with ‘a’.
    
4. Display total salary of Developers.
    
5. Display all names in uppercase.
    
6. Display employee with maximum salary.
    
7. Display staff whose names contain ‘ha’.
    
8. Display minimum salary in the table.
    
9. Sort employees by Salary in descending order.
    
10. Display employees born before 1990.
    

---

# 3. Worker Table

|Wid|Wname|DeptId|Designation|Salary|DOJ|
|---|---|---|---|---|---|
|201|Arjun|D1|Clerk|25000|01-Jan-14|
|202|Sneha|D2|Manager|65000|10-Oct-19|
|203|Karthik|D3|Accountant|40000|15-Jul-16|
|204|Priya|D1|Salesman|30000|18-Feb-18|
|205|Nitin|D2|Clerk|27000|25-May-17|

## Department Table

|DeptId|Dname|
|---|---|
|D1|Sales|
|D2|HR|
|D3|Accounts|

### Questions

1. Display employees earning more than average salary.
    
2. Display Wid, Wname and Department name.
    
3. Sort workers by salary descending.
    
4. Display distinct designations.
    
5. Display worker details department-wise.
    
6. Display clerks in D2 department.
    
7. Display employees joined in 2018.
    
8. Display highest salary department-wise.
    
9. Display total salary department-wise.
    
10. Display employees whose names start with ‘P’.
    

---

# 4. BookStore Table

|BookId|BookName|Author|PurchaseDate|Publisher|Price|
|---|---|---|---|---|---|
|BK101|Java Basics|Herbert Schildt|12-Jan-18|Pearson|650|
|BK102|Python Guide|Mark Lutz|22-Mar-20|McGrawHill|720|
|BK103|DBMS Concepts|Korth|15-Jul-19|TMH|880|
|BK104|Data Structures|Lipschutz|19-Sep-17|Pearson|540|
|BK105|Networking|Forouzan|05-Dec-21|Wiley|900|

### Questions

1. Display books published by Pearson.
    
2. Display total cost publisher-wise.
    
3. Count total books under TMH publication.
    
4. Rename column Publisher as Publications.
    
5. Display books in ascending order of purchase date.
    
6. Create an index on BookName and Author.
    
7. Display books priced between 600 and 900.
    
8. Display books costing above average price.
    
9. Display authors whose names start with ‘M’.
    
10. Display minimum and maximum book prices.
    

---

# 5. CollegeStudent Table

|Sid|Sname|DOB|State|Gender|Category|Course|
|---|---|---|---|---|---|---|
|2001|Asha|11-Feb-03|Kerala|F|Gen|BCA|
|2002|Rohit|20-Jun-02|Karnataka|M|OBC|BCom|
|2003|Nisha|05-Oct-01|Tamil Nadu|F|Gen|BSc|
|2004|Varun|17-Dec-03|Kerala|M|Sports|BCA|
|2005|Pooja|29-Aug-02|Andhra Pradesh|F|OBC|BCom|

### Questions

1. Display students not from Kerala.
    
2. Create a view showing Sid and Sname of Kerala students.
    
3. Create an index on Sname.
    
4. Display female students in BCom course.
    
5. Display student age.
    
6. Sort students course-wise and name-wise.
    
7. Delete students enrolled in BCA born after 2002.
    
8. Display students belonging to OBC category.
    
9. Display distinct states.
    
10. Count total female students.
    

---

# 6. Employee Table

|Emp_Id|Emp_Name|Department|Salary|City|
|---|---|---|---|---|
|E1|Arjun|HR|35000|Chennai|
|E2|Meera|Finance|42000|Delhi|
|E3|Kiran|IT|50000|Bangalore|
|E4|Sneha|HR|37000|Mumbai|
|E5|Rahul|Marketing|30000|Pune|
|E6|Anita|IT|52000|Hyderabad|

### Questions

1. Create Employee table using CQL.
    
2. Insert all records into Employee table.
    
3. Retrieve all records from Employee table.
    
4. Display employees working in IT department.
    
5. Update salary of employee E5 from 30000 to 35000.
    
6. Delete record of employee E2.
    
7. Delete all employees located in Chennai.
    
8. Display employees whose salary is greater than 40000.
    
9. Display employee names in ascending order.
    
10. Count total number of employees.
    

---

# 7. Student Table

|Stu_Id|Stu_Name|Course|Fees|State|
|---|---|---|---|---|
|ST1|Neha|BCA|25000|Kerala|
|ST2|Rohit|BCom|22000|Karnataka|
|ST3|Pooja|BSc|27000|Tamil Nadu|
|ST4|Akhil|BCA|26000|Andhra Pradesh|
|ST5|Ramya|BCom|24000|Telangana|
|ST6|Varun|BCA|25500|Kerala|

### Questions

1. Create Student table using CQL.
    
2. Insert all records into Student table.
    
3. Retrieve all records from Student table.
    
4. Display students studying BCA.
    
5. Update fees of student ST2 from 22000 to 23000.
    
6. Delete record of student ST5.
    
7. Delete all students belonging to Kerala.
    
8. Display students whose fees are greater than 25000.
    
9. Display student names in alphabetical order.
    
10. Count total number of students.
    

---

# 8. Book Table

|Book_Id|Book_Name|Author|Price|Publisher|
|---|---|---|---|---|
|B1|Java Basics|Herbert Schildt|650|Pearson|
|B2|Python Guide|Mark Lutz|700|McGrawHill|
|B3|DBMS Concepts|Korth|850|TMH|
|B4|Data Structures|Lipschutz|500|Pearson|
|B5|Operating Systems|Galvin|900|Wiley|
|B6|Networking|Forouzan|750|TMH|

### Questions

1. Create Book table using CQL.
    
2. Insert all records into Book table.
    
3. Retrieve all records from Book table.
    
4. Display books published by TMH.
    
5. Update price of book B4 from 500 to 650.
    
6. Delete record of book B2.
    
7. Delete all books published by Pearson.
    
8. Display books costing more than 700.
    
9. Display book names in ascending order.
    
10. Count total number of books.
    

---

# 9. Product Table

|Product_Id|Product_Name|Category|Price|Company|
|---|---|---|---|---|
|P1|Refrigerator|Electronics|30000|LG|
|P2|Washing Machine|Electronics|25000|Samsung|
|P3|Sofa|Furniture|18000|HomeStyle|
|P4|Laptop|Electronics|55000|Dell|
|P5|Dining Table|Furniture|20000|UrbanWood|
|P6|Television|Electronics|40000|Sony|

### Questions

1. Create Product table using CQL.
    
2. Insert all records into Product table.
    
3. Retrieve all records from Product table.
    
4. Display products under Electronics category.
    
5. Update price of product P3 from 18000 to 22000.
    
6. Delete record of product P5.
    
7. Delete all products belonging to company LG.
    
8. Display products whose price is greater than 30000.
    
9. Display product names in alphabetical order.
    
10. Count total number of products.
    

---

# 10. SupplierInfo Table

|Supplier_ID|Supplier_Name|Product_Name|Price|Location|
|---|---|---|---|---|
|SP1|Nikhil|Scanner|4500|Hyderabad|
|SP2|Ramesh|Laptop|55000|Chennai|
|SP3|Vinay|Printer|9000|Delhi|
|SP4|Kunal|Mouse|800|Mumbai|
|SP5|Sagar|Laptop|60000|Bangalore|

### Questions

1. Display Supplier IDs and Supplier names whose names start with ‘S’.
    
2. Display suppliers supplying Laptop from Chennai.
    
3. Increase the price of Mouse by 200.
    
4. Display supplier details from Delhi sorted by price.
    
5. Add a column named PhoneNo.
    
6. Delete the record having the lowest price.
    
7. Display distinct locations from the table.
    
8. Create an index on Supplier_Name.
    
9. Display products costing more than 5000.
    
10. Count total number of suppliers.
    

---

# 11. EmployeeDetails Table

|Emp_ID|Emp_Name|DOB|Designation|Salary|DOJ|
|---|---|---|---|---|---|
|E201|Anoop|15-Jan-91|Analyst|48000|12-Jun-16|
|E202|Divya|20-Mar-95|Developer|52000|18-Aug-20|
|E203|Harish|12-Jul-88|Tester|35000|25-May-14|
|E204|Megha|08-Sep-90|HR|40000|11-Apr-18|
|E205|Rohan|10-Dec-85|Manager|75000|05-Jan-12|

### Questions

1. Display all Developers.
    
2. Display employees who joined after 2018.
    
3. Display employee names ending with ‘a’.
    
4. Display total salary of Analysts.
    
5. Display employee with minimum salary.
    
6. Sort employees by Salary in ascending order.
    
7. Display distinct designations.
    
8. Delete employees whose designation is Tester.
    
9. Display employees earning more than 50000.
    
10. Count total number of employees.
    

---

# 12. Staff Table

|Staff_ID|Staff_Name|DeptId|Designation|Salary|DOJ|
|---|---|---|---|---|---|
|301|Aravind|D1|Clerk|22000|01-Feb-15|
|302|Neethu|D2|Manager|68000|12-Oct-19|
|303|Sanjay|D3|Accountant|45000|25-Jul-17|
|304|Priyanka|D1|Salesman|32000|18-Jan-18|
|305|Vivek|D2|Clerk|28000|05-May-16|

## Department Table

|DeptId|Dept_Name|
|---|---|
|D1|Sales|
|D2|Finance|
|D3|Accounts|

### Questions

1. Display employees earning more than average salary.
    
2. Display Staff_ID, Staff_Name and Department name.
    
3. Sort staff by salary descending.
    
4. Display distinct designations.
    
5. Display staff details department-wise.
    
6. Display clerks in D2 department.
    
7. Display employees joined in 2018.
    
8. Display count of employees in each department.
    
9. Display employees whose names start with ‘P’.
    
10. Display employees with salary less than 30000.
    

---

# 13. LibraryBooks Table

|Book_ID|Book_Name|Author|Purchase_Date|Publisher|Price|
|---|---|---|---|---|---|
|LB101|C Programming|Balagurusamy|12-Jan-18|McGrawHill|650|
|LB102|Python Basics|Mark Lutz|15-Mar-20|Pearson|750|
|LB103|Database Systems|Navathe|10-Jul-19|TMH|850|
|LB104|Operating System|Galvin|22-Sep-17|Wiley|550|
|LB105|Computer Networks|Forouzan|30-Nov-21|Pearson|920|

### Questions

1. Display books published by Pearson.
    
2. Display total cost publisher-wise.
    
3. Count total books under TMH publication.
    
4. Rename column Publisher as Publications.
    
5. Display books in ascending order of purchase date.
    
6. Create an index on Book_Name and Author.
    
7. Display books priced between 600 and 900.
    
8. Delete books priced below 600.
    
9. Display books costing more than average price.
    
10. Display distinct publishers from the table.