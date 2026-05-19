

`SHOW` commands are used to display information about databases and tables.

These are super common in lab exams and viva 😭

---

# 1. SHOW DATABASES 🗂️

Used to display all databases present in the DBMS.

---

## Syntax

```sql
SHOW DATABASES;
```

---

## Example Output

|Database|
|---|
|college|
|library|
|company|

---

## What it does

Displays all available databases in the system.

---

# 2. SHOW TABLES 📋

Used to display all tables inside the currently selected database.

---

## Syntax

```sql
SHOW TABLES;
```

---

## Example Output

|Tables_in_college|
|---|
|student|
|employee|
|marks|

---

## What it does

Shows all tables in the current database.

---

# Important Thing 🚨

Before using `SHOW TABLES`, select a database using:

```sql
USE college;
```

Otherwise DBMS may throw error like:

> No database selected 💀

---

# Full Example Flow

```sql
SHOW DATABASES;

USE college;

SHOW TABLES;
```

---

# Related Commands 🔥

---

## Select Database

```sql
USE college;
```

Changes current working database.

---

## Describe Table Structure

```sql
DESC student;
```

OR

```sql
DESCRIBE student;
```

---

## Example Output

|Field|Type|
|---|---|
|rollno|INT|
|name|VARCHAR(30)|

---

# Possible Viva Questions 🎤

## Q1. Which command displays all databases?

`SHOW DATABASES;`

---

## Q2. Which command displays tables in a database?

`SHOW TABLES;`

---

## Q3. Why is USE command needed?

To select the database before working on tables.

---

## Q4. What happens if SHOW TABLES is used without selecting database?

DBMS gives error.

---

## Q5. Which command shows table structure?

`DESC table_name;`

---

## Q6. Is SHOW a DDL command?

No. It is an administrative/display command.

---

## Q7. Difference between SHOW DATABASES and SHOW TABLES?

|SHOW DATABASES|SHOW TABLES|
|---|---|
|Displays databases|Displays tables|

---

# Common Lab Flow 🧪

```sql
SHOW DATABASES;

CREATE DATABASE college;

USE college;

CREATE TABLE student (
    rollno INT,
    name VARCHAR(30)
);

SHOW TABLES;

DESC student;
```

---

# Teacher Trap Questions 😭

### “Can SHOW TABLES display tables from all databases?”

No. Only current database.

---

### “Does SHOW DATABASES create databases?”

No. It only displays them.

---

# Quick Revision ⚡

|Command|Purpose|
|---|---|
|SHOW DATABASES|Shows all databases|
|USE database_name|Selects database|
|SHOW TABLES|Shows tables|
|DESC table_name|Shows table structure|