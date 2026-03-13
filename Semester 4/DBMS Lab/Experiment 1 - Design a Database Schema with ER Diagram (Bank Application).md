
# 1. Aim of the Experiment

To **design a database schema and ER diagram for a bank management system** based on a given problem description.

The database stores information about:

- Bank branches
    
- Customers
    
- Accounts
    
- Transactions
    
- Loans
    

It also models **relationships between these entities**.

---

# 2. Core DBMS Concepts Used

This experiment mainly demonstrates:

- **Entity Relationship (ER) modeling**
    
- **Relational schema design**
    
- **Primary keys**
    
- **Foreign keys**
    
- **Many-to-many relationships**
    
- **Referential integrity**
    
- **Database schema creation using SQL**
    

---

# 3. Entities in the System

The system contains **7 tables**.

|Entity|Purpose|
|---|---|
|Branch|Stores bank branch details|
|Customer|Stores customer details|
|Account|Stores bank account details|
|Transaction|Stores account transactions|
|Loan|Stores loan information|
|CustomerAccount|Links customers and accounts|
|CustomerLoan|Links customers and loans|

---

# 4. SQL Code Explanation

---

# Step 1: Create Database

```
create database bank;  
use bank;
```
Explanation:

- `create database bank` → Creates a new database named **bank**
    
- `use bank` → Selects the **bank database** to work with
    

---

# Step 2: Create Branch Table

```
CREATE TABLE Branch (  
branch_id INT PRIMARY KEY,  
branch_name VARCHAR(100),  
branch_address VARCHAR(255)  
);
```

Explanation:

- `CREATE TABLE` → Creates a new table
    
- `Branch` → Table name
    
- `branch_id INT` → Unique identifier for each branch
    
- `PRIMARY KEY` → Ensures every branch has a **unique ID**
    
- `branch_name` → Name of the branch
    
- `branch_address` → Address of the branch
    

Purpose:  
Stores information about **bank branches**.

Example data:

|branch_id|branch_name|branch_address|
|---|---|---|
|101|SBI Kochi|MG Road|

---

# Step 3: Create Customer Table

```
CREATE TABLE Customer (  
customer_id INT PRIMARY KEY,  
name VARCHAR(100),  
address VARCHAR(255),  
phone VARCHAR(15),  
email VARCHAR(100)  
);
```

Explanation:

- `customer_id` → Unique identifier for each customer
    
- `PRIMARY KEY` → Ensures unique customer records
    
- `name` → Customer name
    
- `address` → Customer address
    
- `phone` → Contact number
    
- `email` → Email address
    

Purpose:  
Stores details of **bank customers**.

---

# Step 4: Create Account Table

```
CREATE TABLE Account (  
account_id INT PRIMARY KEY,  
account_type VARCHAR(50),  
balance DECIMAL(15,2),  
branch_id INT,  
FOREIGN KEY (branch_id) REFERENCES Branch(branch_id)  
);
```

Explanation:

- `account_id` → Unique account number
    
- `account_type` → Type of account (Savings / Current)
    
- `balance` → Current balance in account
    
- `branch_id` → Identifies which branch owns the account
    
- `FOREIGN KEY` → Links this table to **Branch table**
    

Meaning:

Each account **must belong to a branch**.

---

# Step 5: Create CustomerAccount Table

```
CREATE TABLE CustomerAccount (  
customer_id INT,  
account_id INT,  
PRIMARY KEY (customer_id, account_id),  
FOREIGN KEY (customer_id) REFERENCES Customer(customer_id),  
FOREIGN KEY (account_id) REFERENCES Account(account_id)  
);
```

Purpose:

Handles **many-to-many relationship** between:

Customer ↔ Account

Why?

- One customer → many accounts
    
- One account → many customers (joint account)
    

Explanation:

- `PRIMARY KEY (customer_id, account_id)` → Composite key
    
- Prevents duplicate relationships
    

Example:

|customer_id|account_id|
|---|---|
|1|1001|
|2|1001|

Joint account.

---

# Step 6: Create Transaction Table

```
CREATE TABLE Transaction (  
transaction_id INT PRIMARY KEY,  
account_id INT,  
transaction_type VARCHAR(50),  
amount DECIMAL(15,2),  
transaction_date DATE,  
FOREIGN KEY (account_id) REFERENCES Account(account_id)  
);
```
Explanation:

- `transaction_id` → Unique transaction number
    
- `account_id` → Account on which transaction occurred
    
- `transaction_type` → Deposit or Withdrawal
    
- `amount` → Amount of money
    
- `transaction_date` → Date of transaction
    
- `FOREIGN KEY` → Links transaction to account
    

Meaning:

Transactions occur **only on accounts**.

---

# Step 7: Create Loan Table

```
CREATE TABLE Loan (  
loan_id INT PRIMARY KEY,  
loan_type VARCHAR(50),  
amount DECIMAL(15,2),  
branch_id INT,  
FOREIGN KEY (branch_id) REFERENCES Branch(branch_id)  
);
```
Explanation:

- `loan_id` → Unique loan identifier
    
- `loan_type` → Home loan, car loan, etc.
    
- `amount` → Loan amount
    
- `branch_id` → Branch issuing the loan
    

Meaning:

Every loan is issued by **one branch**.

---

# Step 8: Create CustomerLoan Table

```
CREATE TABLE CustomerLoan (  
customer_id INT,  
loan_id INT,  
PRIMARY KEY (customer_id, loan_id),  
FOREIGN KEY (customer_id) REFERENCES Customer(customer_id),  
FOREIGN KEY (loan_id) REFERENCES Loan(loan_id)  
);
```

Purpose:

Handles **many-to-many relationship** between:

$$
Customer ↔ Loan
$$

Example:

Business loan shared by partners.

---

# 5. Relationships and Cardinality

|Relationship|Type|
|---|---|
|Branch → Account|1 : N|
|Branch → Loan|1 : N|
|Customer → Account|M : N|
|Account → Transaction|1 : N|
|Customer → Loan|M : N|

---

# 6. Why Junction Tables Are Used

Tables:

- `CustomerAccount`
    
- `CustomerLoan`
    

These resolve **many-to-many relationships**.

Without them relational databases **cannot represent M:N relationships directly**.

---

# 7. Possible Viva Questions (With Answers)

---

### Q1. What is an ER diagram?

**Answer**

An ER diagram (Entity Relationship diagram) is a graphical representation of entities, attributes, and relationships in a database.

---

### Q2. What is an entity?

**Answer**

An entity is a real-world object that can be uniquely identified in a database.

Example: Customer, Account.

---

### Q3. What is an attribute?

**Answer**

An attribute is a property or characteristic of an entity.

Example: customer name, phone number.

---

### Q4. What is a primary key?

**Answer**

A primary key is a column that uniquely identifies each record in a table and cannot contain NULL values.

---

### Q5. What is a foreign key?

**Answer**

A foreign key is a column that creates a relationship between two tables by referencing the primary key of another table.

---

### Q6. What is cardinality?

**Answer**

Cardinality defines the number of relationships between entities.

Examples:

- One-to-One
    
- One-to-Many
    
- Many-to-Many
    

---

### Q7. Why is CustomerAccount table needed?

**Answer**

It resolves the many-to-many relationship between customers and accounts.

---

### Q8. What is a composite key?

**Answer**

A composite key is a primary key made from **two or more columns**.

Example:

(customer_id, account_id)

---

### Q9. Why do we use foreign keys?

**Answer**

Foreign keys maintain **referential integrity** between tables.

---

### Q10. What is referential integrity?

**Answer**

Referential integrity ensures that a foreign key value always refers to an existing record in the parent table.

---

### Q11. Why are transactions linked only to accounts?

**Answer**

Because deposits and withdrawals happen only on bank accounts, not on loans.

---

### Q12. What is a relational schema?

**Answer**

A relational schema defines the structure of tables, attributes, and relationships in a relational database.

---

### Q13. What is normalization?

**Answer**

Normalization is the process of organizing data to reduce redundancy and improve data integrity.

---

### Q14. What is reverse engineering in DBMS?

**Answer**

Reverse engineering is the process of generating an ER diagram from an existing database schema.

---

# 8. Very Tricky Viva Questions (Teachers Love These)

---

### Q: Can a table have multiple primary keys?

Answer:  
No. A table can have only **one primary key**, but it may consist of multiple columns.

---

### Q: Can a foreign key be NULL?

Answer:  
Yes, unless it is defined with a **NOT NULL constraint**.

---

### Q: What happens if we delete a referenced record?

Answer:  
It may cause **referential integrity violation** unless cascading rules are used.


---


[[DBMS Lab Experiments]]