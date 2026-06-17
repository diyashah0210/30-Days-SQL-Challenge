# 🚀 30 Days of SQL – Day 22: Assessment 3

Welcome to **Day 22** of the **30 Days of SQL Challenge!**

Today is an assessment day designed to test your understanding of:

- CTEs & Recursive CTEs
- Views & Materialized Views
- Indexes & Query Optimization
- Transactions & Concurrency Control

---

# 📚 Assessment Structure

| Section | Questions | Marks |
|----------|----------|----------|
| MCQs | 15 | 15 |
| Practical SQL Problems | 15 | 15 |
| Total | 30 | 30 |

---

# Part A: Multiple Choice Questions (15 Marks)

### 1. What does CTE stand for?

A. Common Table Expression

B. Common Transaction Entity

C. Column Table Expression

D. Conditional Table Engine

---

### 2. Which keyword is used to create a CTE?

A. CREATE

B. WITH

C. BEGIN

D. TEMP

---

### 3. A View is:

A. Physical Table

B. Temporary Table

C. Virtual Table

D. Stored Procedure

---

### 4. Which command permanently saves a transaction?

A. SAVEPOINT

B. COMMIT

C. ROLLBACK

D. LOCK

---

### 5. Which command undoes a transaction?

A. COMMIT

B. SAVEPOINT

C. ROLLBACK

D. DELETE

---

### 6. Which index is automatically created on a PRIMARY KEY?

A. Full Text Index

B. Composite Index

C. Primary Index

D. Non-Clustered Index

---

### 7. Which SQL command helps analyze query execution plans?

A. DESCRIBE

B. EXPLAIN

C. ANALYZE TABLE

D. SHOW

---

### 8. Which index contains multiple columns?

A. Composite Index

B. Clustered Index

C. Unique Index

D. Full Text Index

---

### 9. Which ACID property ensures all operations succeed or fail together?

A. Consistency

B. Isolation

C. Atomicity

D. Durability

---

### 10. Which ACID property ensures committed data survives a crash?

A. Atomicity

B. Consistency

C. Isolation

D. Durability

---

### 11. Which type of View physically stores data?

A. Simple View

B. Complex View

C. Materialized View

D. Recursive View

---

### 12. Which problem occurs when one transaction reads uncommitted data?

A. Phantom Read

B. Dirty Read

C. Deadlock

D. Lost Update

---

### 13. Which isolation level prevents Dirty Reads, Non-Repeatable Reads, and Phantom Reads?

A. Read Uncommitted

B. Read Committed

C. Repeatable Read

D. Serializable

---

### 14. What happens if a Recursive CTE lacks a termination condition?

A. Syntax Error

B. NULL Result

C. Infinite Recursion

D. Empty Result

---

### 15. What is a Deadlock?

A. Missing Index

B. Duplicate Data

C. Two Transactions Waiting for Each Other

D. Corrupted Table

---

# Part B: Practical SQL Problems (15 Marks)

### 16.

Create a CTE that displays employees earning more than ₹60,000.

---

### 17.

Create a View named `Employee_View` displaying:

- Employee ID
- Employee Name
- Department

---

### 18.

Create an index on the `customer_id` column of an Orders table.

---

### 19.

Start a transaction and update an employee's salary.

---

### 20.

Use COMMIT to save the transaction.

---

### 21.

Create two CTEs in a single query:

- Department Average Salary
- Employee Count

Display both results.

---

### 22.

Create a View using an INNER JOIN between Employees and Departments.

---

### 23.

Create a Composite Index on:

- customer_id
- order_date

---

### 24.

Use EXPLAIN to analyze:

```sql
SELECT *
FROM Orders
WHERE customer_id = 101;
```

---

### 25.

Create a SAVEPOINT inside a transaction and rollback to it.

---

### 26.

Create a Recursive CTE generating numbers from 1 to 25.

---

### 27.

Build an employee-manager hierarchy using a Recursive CTE.

Expected Output:

| Employee | Manager |
|-----------|-----------|

---

### 28.

Create a Materialized View showing monthly sales totals.

Expected Output:

| Month | Total Sales |
|---------|------------|

---

### 29.

A query filters by:

```sql
customer_id
AND
order_date
```

Design the best indexing strategy and write the SQL statement.

---

### 30.

Design a complete banking transaction workflow using:

- START TRANSACTION
- UPDATE
- SAVEPOINT
- COMMIT
- ROLLBACK

for transferring ₹5,000 from Account A to Account B.

---

# 📖 Day 22 Summary

Congratulations! 🎉

You've now completed four major SQL assessments covering:

- Query Writing
- Data Analysis
- Database Design
- Performance Optimization
- Transaction Management
---

## 🚀 Coming Up Next: Day 23 – Triggers & Events

## Progress Status: Day 22 Completed ✅

---
[ANSWERS]()

[PREVIOUS: DAY21-Transaction and Concurrency Control]()👆\
[NEXT: DAY23-TRIGGERS AND EVENTS](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/d6e86f277540ce8b7e65f46fedb0632217281561/DAY23/DAY23-%20Data%20Modeling%20%26%20Normalization.md)👇
