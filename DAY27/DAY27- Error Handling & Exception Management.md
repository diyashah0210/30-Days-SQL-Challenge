# 📘 30 Days Of SQL: Day 27 - Error Handling & Exception Management

Welcome to **Day 27** of the **30 Days of SQL** challenge! 🎉

No matter how well-designed a database is, errors are inevitable. Data may violate constraints, transactions may fail, users may enter invalid values, or system failures may interrupt operations.

Today, you'll learn how professional database systems handle errors gracefully using **Error Handling**, **Exception Management**, **Transaction Rollbacks**, and **Logging Mechanisms**.

These concepts are essential for building reliable, production-ready database applications.

---

# 📚 Table of Contents

1. Overview
2. What is Error Handling?
3. Why Error Handling is Important
4. Types of SQL Errors
5. Understanding Exceptions
6. Syntax Errors
7. Constraint Violations
8. Data Type Errors
9. Transaction Errors
10. Runtime Errors
11. TRY...CATCH Blocks
12. THROW and RAISEERROR
13. Transaction Rollbacks
14. Error Logging
15. Custom Error Messages
16. Debugging SQL Queries
17. Best Practices
18. Real-World Use Cases
19. Common Mistakes
20. Hands-On Challenge
21. Practice Exercises
22. Key Takeaways
23. Day 27 Summary

---

# 🔍 Overview

Error handling helps prevent database failures from causing:

❌ Data Corruption

❌ Incomplete Transactions

❌ Application Crashes

❌ Inconsistent Records

Instead of allowing failures to break the system, SQL can detect and manage them appropriately.

---

# 📌 What is Error Handling?

Error Handling is the process of detecting, managing, and responding to errors during SQL execution.

Example:

```sql
INSERT INTO Employees
VALUES (1, 'John', -5000);
```

A negative salary may violate business rules.

Instead of accepting invalid data, the database should raise an error.

---

# 🎯 Why Error Handling is Important

Benefits:

✅ Prevents Invalid Data

✅ Maintains Data Integrity

✅ Protects Transactions

✅ Improves Reliability

✅ Simplifies Debugging

✅ Enhances User Experience

---

# ⚠ Types of SQL Errors

| Error Type | Description |
|------------|-------------|
| Syntax Errors | Incorrect SQL syntax |
| Constraint Errors | Violating constraints |
| Data Type Errors | Wrong data format |
| Runtime Errors | Occur during execution |
| Transaction Errors | Failed transactions |
| Permission Errors | Unauthorized access |

---

# 1️⃣ Syntax Errors

These occur when SQL statements are written incorrectly.

Example:

```sql
SELEC *
FROM Employees;
```

Error:

```text
Unknown keyword 'SELEC'
```

Correct:

```sql
SELECT *
FROM Employees;
```

---

# 2️⃣ Constraint Violations

Occur when constraints are violated.

Example:

```sql
CREATE TABLE Employees
(
    EmployeeID INT PRIMARY KEY,
    Email VARCHAR(100) UNIQUE
);
```

Insert:

```sql
INSERT INTO Employees
VALUES (1,'john@gmail.com');

INSERT INTO Employees
VALUES (2,'john@gmail.com');
```

Result:

```text
Duplicate Entry Error
```

---

# 3️⃣ Data Type Errors

Occurs when incorrect data types are inserted.

Example:

```sql
INSERT INTO Employees
(EmployeeID)
VALUES ('ABC');
```

If EmployeeID is INT:

```text
Invalid Integer Error
```

---

# 4️⃣ Transaction Errors

Occurs when part of a transaction fails.

Example:

```sql
BEGIN TRANSACTION;

UPDATE Accounts
SET Balance = Balance - 1000
WHERE AccountID = 1;

UPDATE Accounts
SET Balance = Balance + 1000
WHERE AccountID = 999;

COMMIT;
```

If AccountID 999 does not exist:

```text
Transaction Failure
```

---

# 5️⃣ Runtime Errors

Occur while executing valid SQL.

Example:

```sql
SELECT 100 / 0;
```

Result:

```text
Division By Zero Error
```

---

# 🚨 Understanding Exceptions

An Exception is an unexpected condition that interrupts normal execution.

Examples:

- Duplicate Keys
- Invalid Dates
- Missing Tables
- Arithmetic Errors

Good systems anticipate and handle exceptions gracefully.

---

# 🛡 TRY...CATCH Blocks

Many databases support TRY...CATCH structures.

Example:

```sql
BEGIN TRY

    INSERT INTO Employees
    VALUES (1,'John');

END TRY

BEGIN CATCH

    PRINT 'Error Occurred';

END CATCH;
```

Flow:

```text
TRY
 ↓
Success → Continue

Failure → CATCH
```

---

# 🎯 Capturing Error Details

SQL Server Example:

```sql
BEGIN CATCH

SELECT
    ERROR_NUMBER() AS ErrorNumber,
    ERROR_MESSAGE() AS ErrorMessage;

END CATCH;
```

Useful for:

- Debugging
- Logging
- Monitoring

---

# 🚫 THROW Statement

Used to generate custom exceptions.

Example:

```sql
IF @Salary < 0
THROW 50001,
'Salary cannot be negative',
1;
```

Result:

```text
Salary cannot be negative
```

---

# 🚫 RAISERROR Statement

Older SQL Server error mechanism.

Example:

```sql
RAISERROR(
'Invalid Employee ID',
16,
1
);
```

---

# 🔄 Transaction Rollbacks

One of the most important concepts in SQL.

When something fails:

```text
Undo Everything
```

---

## Example Without Rollback

```sql
UPDATE AccountA
SET Balance = Balance - 1000;

-- Failure occurs

UPDATE AccountB
SET Balance = Balance + 1000;
```

Money disappears.

---

## Example With Rollback

```sql
BEGIN TRANSACTION;

BEGIN TRY

    UPDATE AccountA
    SET Balance = Balance - 1000;

    UPDATE AccountB
    SET Balance = Balance + 1000;

    COMMIT;

END TRY

BEGIN CATCH

    ROLLBACK;

END CATCH;
```

Database remains consistent.

---

# 📝 Error Logging

Production systems log errors for later analysis.

Example Table:

```sql
CREATE TABLE Error_Log
(
    Error_ID INT IDENTITY(1,1),
    Error_Message VARCHAR(500),
    Error_Time DATETIME
);
```

Insert Log:

```sql
INSERT INTO Error_Log
(
    Error_Message,
    Error_Time
)
VALUES
(
    ERROR_MESSAGE(),
    GETDATE()
);
```

---

# 🎨 Custom Error Messages

Example:

```sql
IF @Age < 18

THROW 50002,
'Employee must be at least 18 years old',
1;
```

Benefits:

✅ Better User Feedback

✅ Easier Troubleshooting

---

# 🐞 Debugging SQL Queries

Steps:

### Step 1

Verify Syntax

```sql
SELECT *
FROM Employees;
```

---

### Step 2

Check Data Types

---

### Step 3

Validate Constraints

---

### Step 4

Test Small Queries First

---

### Step 5

Review Error Messages Carefully

---

# 🏢 Real-World Use Cases

## Banking

Rollback failed money transfers.

---

## E-Commerce

Prevent duplicate orders.

---

## Healthcare

Validate patient records.

---

## Payroll

Prevent negative salaries.

---

## Inventory Systems

Block negative stock quantities.

---

# ❌ Common Mistakes

### Ignoring Error Messages

Always read the complete error.

---

### No Transaction Rollbacks

Can leave data partially updated.

---

### Generic Error Handling

Makes debugging difficult.

---

### No Logging Mechanism

Problems become harder to investigate.

---

### Exposing Internal Errors to Users

Can create security risks.

---

# 🔧 Best Practices

✅ Always use transactions for critical operations

✅ Implement TRY...CATCH blocks

✅ Log important errors

✅ Create meaningful error messages

✅ Validate data before insertion

✅ Use rollbacks when failures occur

✅ Monitor production error logs

---

# 🎨 Hands-On Challenge

1. Create a TRY...CATCH block for employee insertion.
2. Create custom salary validation.
3. Build an error logging table.
4. Implement transaction rollback for fund transfers.
5. Generate custom exceptions using THROW.

---

# 💻 Practice Exercises

## ✅ Level 1

1. Identify syntax errors in SQL statements.
2. Create a TRY...CATCH block.
3. Log an error into a table.
4. Generate a custom exception.
5. Handle a division-by-zero error.

---

## 🚀 Level 2

1. Create a complete employee validation system.
2. Implement banking transaction rollbacks.
3. Build an audit and error logging framework.
4. Design a centralized exception handling mechanism.
5. Create custom business-rule validations.

---

# 🎯 Key Takeaways

✅ Errors are inevitable in database systems.

✅ Error handling improves reliability and stability.

✅ TRY...CATCH blocks manage exceptions gracefully.

✅ THROW and RAISERROR generate custom errors.

✅ Rollbacks protect data consistency.

✅ Logging helps diagnose production issues.

✅ Proper error handling is a hallmark of enterprise-grade systems.

---

# 📝 Day 27 Summary

Today, you learned how SQL databases handle errors, exceptions, transaction failures, and runtime issues. You explored TRY...CATCH blocks, custom exceptions, rollback mechanisms, logging systems, and debugging techniques.

These concepts are critical in enterprise applications where reliability, consistency, and fault tolerance are essential.

---

## 🚀 Coming Up Next: Day 28 – SQL Security & User Management

### Topics Covered

- Database Security Fundamentals
- Authentication vs Authorization
- Users & Roles
- GRANT and REVOKE
- Data Protection
- SQL Injection Prevention
- Row-Level Security
- Encryption Basics
- Security Best Practices

## Progress Status: Day 27 Completed ✅
[PREVIOUS: DAY26-SQL FOR ANALYTICS](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/c89b78382d4335e196e8a8f92bf9b1edbf93d5b2/DAY26/DAY26-%20SQL%20for%20Analytics.md) 👆\
[NEXT: DAY28-SQL SECURITY AND USER MANAGEMENT](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/c89b78382d4335e196e8a8f92bf9b1edbf93d5b2/DAY28/DAY28-%20SQL%20Security%20%26%20User%20Management.md) 👇
