# 🚀 30 Days of SQL – Day 21: Transactions & Concurrency Control

Welcome to **Day 21** of the **30 Days of SQL Challenge**!

In real-world applications such as banking, e-commerce, healthcare, and financial systems, data integrity is critical. Imagine transferring money from one account to another and the system crashes midway.

How do databases ensure data remains accurate and consistent?

The answer lies in **Transactions** and **Concurrency Control**.

Today, you'll learn one of the most important concepts in SQL and Database Management Systems.

---

# 📚 Table of Contents

1. Introduction to Transactions
2. Why Transactions Are Important
3. Transaction Lifecycle
4. ACID Properties
5. BEGIN / START TRANSACTION
6. COMMIT
7. ROLLBACK
8. SAVEPOINT
9. Transaction Flow
10. Concurrency Control
11. Why Concurrency Control Is Needed
12. Transaction States
13. Dirty Read
14. Non-Repeatable Read
15. Phantom Read
16. Isolation Levels
17. Locks in SQL
18. Deadlocks
19. Deadlock Prevention
20. Real-World Use Cases
21. Common Mistakes
22. Practice Exercises
23. Key Takeaways
24. Day 21 Summary

---

# 1️⃣ Introduction to Transactions

A **Transaction** is a sequence of one or more SQL operations executed as a single unit of work.

Either:

✅ All operations succeed

OR

❌ None of them succeed

---

### Example

Bank Transfer:

```text
Account A → ₹10,000
Account B → ₹5,000
```

Transfer ₹2,000 from A to B.

Steps:

```sql
UPDATE Accounts
SET balance = balance - 2000
WHERE account_id = 1;

UPDATE Accounts
SET balance = balance + 2000
WHERE account_id = 2;
```

Both statements must succeed together.

---

# 2️⃣ Why Transactions Are Important

Without transactions:

```text
Account A Debited ✅

System Crash ❌

Account B Credited ❌
```

Money disappears.

Transactions prevent such situations.

Benefits:

✅ Data Integrity

✅ Data Consistency

✅ Error Recovery

✅ Multi-User Safety

---

# 3️⃣ Transaction Lifecycle

```text
BEGIN TRANSACTION
       ↓
 Execute SQL Statements
       ↓
COMMIT or ROLLBACK
```

---

# 4️⃣ ACID Properties

ACID is the foundation of reliable database systems.

---

## A – Atomicity

All operations succeed or none succeed.

```text
Transfer Money

Debit Account A ✅
Credit Account B ❌

Result:
Everything Rollbacks
```

---

## C – Consistency

Database moves from one valid state to another.

```text
Before Transfer = ₹15,000

After Transfer = ₹15,000
```

Total money remains unchanged.

---

## I – Isolation

Multiple transactions should not interfere with each other.

---

## D – Durability

Once committed, data remains permanent.

Even after:

- Power Failure
- System Crash
- Server Restart

---

# 5️⃣ BEGIN / START TRANSACTION

Starts a transaction.

### MySQL

```sql
START TRANSACTION;
```

### SQL Standard

```sql
BEGIN TRANSACTION;
```

---

# 6️⃣ COMMIT

Permanently saves all changes.

```sql
START TRANSACTION;

UPDATE Accounts
SET balance = balance - 2000
WHERE account_id = 1;

UPDATE Accounts
SET balance = balance + 2000
WHERE account_id = 2;

COMMIT;
```

---

# 7️⃣ ROLLBACK

Undo all changes since transaction start.

```sql
START TRANSACTION;

UPDATE Accounts
SET balance = balance - 2000
WHERE account_id = 1;

ROLLBACK;
```

Result:

```text
Changes Cancelled
```

---

# 8️⃣ SAVEPOINT

Creates checkpoints inside a transaction.

```sql
START TRANSACTION;

SAVEPOINT Step1;

UPDATE Products
SET price = price + 100;

SAVEPOINT Step2;

DELETE FROM Products;

ROLLBACK TO Step2;
```

---

# 9️⃣ Transaction Flow

```text
BEGIN
  ↓
Query 1
  ↓
Query 2
  ↓
SAVEPOINT
  ↓
Query 3
  ↓
COMMIT / ROLLBACK
```

---

# 🔟 Concurrency Control

Concurrency means:

Multiple users accessing the same data simultaneously.

Example:

```text
ATM Machine
Mobile Banking
Internet Banking
```

All accessing the same account.

---

# 1️⃣1️⃣ Why Concurrency Control Is Needed

Without control:

```text
User A reads ₹10,000

User B reads ₹10,000

User A withdraws ₹3,000

User B withdraws ₹4,000
```

Final balance becomes incorrect.

Concurrency control prevents these conflicts.

---

# 1️⃣2️⃣ Transaction States

```text
Active
 ↓
Partially Committed
 ↓
Committed
```

OR

```text
Active
 ↓
Failed
 ↓
Aborted
```

---

# 1️⃣3️⃣ Dirty Read

Occurs when one transaction reads uncommitted data.

### Example

Transaction A:

```sql
UPDATE Accounts
SET balance = 5000;
```

(Not committed)

Transaction B reads:

```text
5000
```

Transaction A rolls back.

Transaction B read invalid data.

---

# 1️⃣4️⃣ Non-Repeatable Read

Same row returns different values.

Transaction A:

```sql
SELECT balance
FROM Accounts;
```

Transaction B updates balance.

Transaction A runs query again.

Different result appears.

---

# 1️⃣5️⃣ Phantom Read

New rows appear between executions.

Transaction A:

```sql
SELECT *
FROM Orders
WHERE amount > 1000;
```

Transaction B inserts a matching row.

Transaction A reruns query.

Extra row appears.

---

# 1️⃣6️⃣ Isolation Levels

SQL provides four isolation levels.

| Level | Dirty Read | Non-Repeatable Read | Phantom Read |
|---------|------------|--------------------|-------------|
| Read Uncommitted | ❌ Possible | ❌ Possible | ❌ Possible |
| Read Committed | ✅ Prevented | ❌ Possible | ❌ Possible |
| Repeatable Read | ✅ Prevented | ✅ Prevented | ❌ Possible |
| Serializable | ✅ Prevented | ✅ Prevented | ✅ Prevented |

---

# 1️⃣7️⃣ Locks in SQL

Locks prevent multiple users from modifying data simultaneously.

---

## Shared Lock

Allows reading.

```text
Read ✓
Write ✗
```

---

## Exclusive Lock

Allows writing.

```text
Read ✗
Write ✓
```

---

# 1️⃣8️⃣ Deadlocks

A deadlock occurs when two transactions wait for each other forever.

### Example

Transaction A:

```text
Locks Table 1
Needs Table 2
```

Transaction B:

```text
Locks Table 2
Needs Table 1
```

Neither can proceed.

---

# 1️⃣9️⃣ Deadlock Prevention

### Follow Consistent Lock Order

Always lock tables in the same order.

---

### Keep Transactions Short

```text
Short Transaction = Less Locking
```

---

### Commit Quickly

Release locks as soon as possible.

---

# 2️⃣0️⃣ Real-World Use Cases

## Banking

Fund Transfers

---

## E-Commerce

Order Placement

---

## Stock Trading

Share Transactions

---

## Airline Booking

Seat Reservations

---

## Healthcare

Patient Record Updates

---

## Payroll Systems

Salary Processing

---

# 2️⃣1️⃣ Common Mistakes

### ❌ Forgetting COMMIT

Changes remain unconfirmed.

---

### ❌ Overusing Serializable Isolation

Can severely reduce performance.

---

### ❌ Long Transactions

Increase locking issues.

---

### ❌ Ignoring Deadlocks

Can block applications.

---

# 📝 Practice Exercises

### Exercise 1

Create a transaction for transferring money between accounts.

### Exercise 2

Use COMMIT after updating employee salaries.

### Exercise 3

Use ROLLBACK after accidental deletion.

### Exercise 4

Create a SAVEPOINT and rollback to it.

### Exercise 5

Demonstrate Atomicity using a banking example.

### Exercise 6

Demonstrate Consistency using inventory management.

### Exercise 7

Identify a Dirty Read scenario.

### Exercise 8

Identify a Non-Repeatable Read scenario.

### Exercise 9

Identify a Phantom Read scenario.

### Exercise 10

Explain differences between isolation levels.

### Exercise 11

Create a transaction involving multiple tables.

### Exercise 12

Demonstrate lock behavior.

### Exercise 13

Explain a deadlock scenario.

### Exercise 14

Suggest deadlock prevention techniques.

### Exercise 15

Design a transaction workflow for an e-commerce checkout system.

---

# 🎯 Key Takeaways

✅ Transactions group multiple SQL statements into one unit.

✅ ACID ensures reliability and consistency.

✅ COMMIT permanently saves changes.

✅ ROLLBACK undoes changes.

✅ SAVEPOINT creates recovery checkpoints.

✅ Concurrency Control manages simultaneous users.

✅ Isolation Levels control transaction visibility.

✅ Locks protect data integrity.

✅ Deadlocks occur when transactions wait on each other.

✅ Transactions are critical in production systems.

---

# 📖 Day 21 Summary

Today, you learned how SQL transactions ensure reliable and consistent data management through the ACID principles.

You explored transaction control commands such as COMMIT, ROLLBACK, and SAVEPOINT, along with concurrency control concepts including locks, isolation levels, dirty reads, phantom reads, and deadlocks.

These concepts form the backbone of enterprise database systems and are heavily used in banking, e-commerce, finance, healthcare, and other mission-critical applications.

---

## 🚀 Coming Up Next: Day 22– SQL Assessment 2
Topics Covered:
- Common Table Expressions (CTEs)
- Recursive CTEs
- Views
- Materialized Views
- Indexes
- Query Optimization
- Transactions
- ACID Properties
- COMMIT
- ROLLBACK
- SAVEPOINT
- Isolation Levels
- Concurrency Control
- Deadlocks


## Progress Status:** Day 21 Completed ✅**

---

[PREVIOUS: DAY20-INDEXES AND OPTIMIZATION](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/bb85f484106b72d35823339469a51032c4476432/DAY20/DAY20-%20Indexes%20%26%20Query%20Optimization.md)👆\
[NEXT: DAY22- SQL MASTERY ASSESSMENT]()👇
