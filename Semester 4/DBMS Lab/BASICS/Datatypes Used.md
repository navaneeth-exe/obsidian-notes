# Datatypes Used in DBMS 📚

Datatypes define **what kind of data** can be stored in a column.

Example:

- Marks → numbers
    
- Name → text
    
- DOB → date
    

Without datatypes DBMS would become pure chaos 💀

---

# 1. Numeric Datatypes 🔢

Used for numbers.

|Datatype|Description|Example|
|---|---|---|
|INT|Integer values|10, 200|
|SMALLINT|Small integers|5|
|BIGINT|Very large integers|999999999|
|FLOAT|Decimal numbers|45.67|
|DOUBLE|Large decimal precision|99.9999|

---

## Example

```sql
CREATE TABLE Marks (
    studentid INT,
    mark FLOAT
);
```

---

# 2. Character/String Datatypes 🔤

Used for text.

|Datatype|Description|
|---|---|
|CHAR(n)|Fixed-length string|
|VARCHAR(n)|Variable-length string|
|TEXT|Large amount of text|

---

## CHAR vs VARCHAR 🥊

### CHAR

Always reserves fixed memory.

```sql
CHAR(10)
```

If stored value is `"Hi"` → remaining spaces filled automatically.

---

### VARCHAR

Uses only required memory.

```sql
VARCHAR(10)
```

Better for names and emails.

---

## Example

```sql
CREATE TABLE Student (
    name VARCHAR(30),
    gender CHAR(1)
);
```

---

# 3. Date and Time Datatypes 📅

Used for dates and time.

|Datatype|Example|
|---|---|
|DATE|2026-05-19|
|TIME|14:30:00|
|DATETIME|2026-05-19 14:30:00|
|TIMESTAMP|Current system timestamp|

---

## Example

```sql
CREATE TABLE Attendance (
    studentid INT,
    attend_date DATE
);
```

---

# 4. Boolean Datatype ✅❌

Stores:

- TRUE
    
- FALSE
    

Example:

```sql
is_active BOOLEAN
```

---

# 5. Binary Datatypes 💾

Used for images, files, videos.

|Datatype|Purpose|
|---|---|
|BLOB|Binary Large Object|

---

# Example

```sql
CREATE TABLE Photos (
    image BLOB
);
```

---

# Most Common Datatypes for Exams 🚨

|Datatype|Usage|
|---|---|
|INT|Numbers|
|VARCHAR|Names/text|
|CHAR|Fixed text|
|FLOAT|Decimal values|
|DATE|Dates|

These are the ones teachers spam in exams 90% of the time 😭

---

# Full Example Table

```sql
CREATE TABLE Employee (
    empid INT,
    name VARCHAR(30),
    gender CHAR(1),
    salary FLOAT,
    joining_date DATE
);
```

---

# Possible Viva Questions 🎤

## Q1. What is a datatype?

Datatype specifies the type of data a column can store.

---

## Q2. Why are datatypes important?

They ensure correct storage and validation of data.

---

## Q3. Difference between CHAR and VARCHAR?

|CHAR|VARCHAR|
|---|---|
|Fixed length|Variable length|

---

## Q4. Which datatype is used for decimal values?

`FLOAT`

---

## Q5. Which datatype stores dates?

`DATE`

---

## Q6. Which datatype is best for names?

`VARCHAR`

---

## Q7. What is BLOB datatype?

Used to store binary data like images/files.

---

## Q8. Can INT store decimal values?

No.

---

## Q9. Which datatype consumes more memory between CHAR and VARCHAR?

`CHAR` usually consumes more for short strings.

---

## Q10. Which datatype stores very long text?

`TEXT`

---

# Teacher Trap Questions 😭

### “Can phone number be stored as INT?”

Technically yes, but better as VARCHAR because:

- phone numbers may contain `+`
    
- leading zeros can disappear
    

---

### “Why not use VARCHAR for everything?”

Bad for performance and validation.

---

# Quick Revision ⚡

|Datatype|Stores|
|---|---|
|INT|Integers|
|FLOAT|Decimals|
|CHAR|Fixed text|
|VARCHAR|Variable text|
|DATE|Dates|
|BLOB|Binary data|