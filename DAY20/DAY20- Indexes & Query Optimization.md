# 🚀 30 Days of SQL – Day 20: Indexes & Query Optimization

Welcome to **Day 20** of the **30 Days of SQL Challenge**!

As databases grow larger, query performance becomes critical. A query that runs in milliseconds on 1,000 rows may take several seconds or minutes on millions of rows.

Today, we'll learn how **Indexes** help databases retrieve data faster and how **Query Optimization** techniques improve SQL performance.

---

# 📚 Table of Contents

1. Introduction to Indexes
2. Why Are Indexes Important?
3. How Indexes Work
4. Types of Indexes
5. Primary Index
6. Unique Index
7. Clustered Index
8. Non-Clustered Index
9. Composite Index
10. Full-Text Index
11. Creating and Managing Indexes
12. Query Optimization Basics
13. Understanding Query Execution Plans
14. Using EXPLAIN
15. Common Query Performance Problems
16. Optimizing WHERE Clauses
17. Optimizing JOIN Operations
18. Optimizing ORDER BY and GROUP BY
19. Indexing Best Practices
20. Common Mistakes
21. Real-World Optimization Examples
22. Practice Exercises
23. Key Takeaways
24. Day 20 Summary

---

# 1️⃣ Introduction to Indexes

An **Index** is a special database object that improves the speed of data retrieval operations.

Think of an index as the **table of contents in a book**.

Without a table of contents, you scan every page.

With a table of contents, you directly jump to the required section.

---

# 2️⃣ Why Are Indexes Important?

Without indexes, databases perform:

```sql
SELECT *
FROM Orders
WHERE customer_id = 1001;
```

The database may need to scan every row.

This is called a:

### Full Table Scan

```text
Row 1 ❌
Row 2 ❌
Row 3 ❌
...
Row 5000000 ✅
```

Indexes dramatically reduce search time.

Benefits:

✅ Faster SELECT Queries

✅ Faster Filtering

✅ Faster Joins

✅ Faster Sorting

✅ Better Reporting Performance

---

# 3️⃣ How Indexes Work

Indexes store:

```text
Value → Location
```

Example:

| Customer_ID | Row Location |
| ----------- | ------------ |
| 1001        | Row 15       |
| 1002        | Row 48       |
| 1003        | Row 103      |

Instead of searching millions of rows, the database jumps directly to the required location.

---

# 4️⃣ Types of Indexes

Major index types:

1. Primary Index
2. Unique Index
3. Clustered Index
4. Non-Clustered Index
5. Composite Index
6. Full-Text Index

---

# 5️⃣ Primary Index

Automatically created when a PRIMARY KEY is defined.

```sql
CREATE TABLE Customers
(
    customer_id INT PRIMARY KEY,
    customer_name VARCHAR(100)
);
```

Benefits:

✅ Unique Values

✅ Fast Searching

---

# 6️⃣ Unique Index

Prevents duplicate values.

```sql
CREATE UNIQUE INDEX idx_email
ON Customers(email);
```

Example:

```text
abc@gmail.com ✅
abc@gmail.com ❌
```

---

# 7️⃣ Clustered Index

A clustered index determines the physical order of data storage.

```text
1
2
3
4
5
```

Only one clustered index can exist per table.

Commonly created on Primary Keys.

---

# 8️⃣ Non-Clustered Index

Stores a separate structure containing:

```text
Indexed Value → Row Pointer
```

Example:

```sql
CREATE INDEX idx_customer_name
ON Customers(customer_name);
```

A table can contain multiple non-clustered indexes.

---

# 9️⃣ Composite Index

Indexes multiple columns together.

```sql
CREATE INDEX idx_customer_order
ON Orders(customer_id, order_date);
```

Useful for queries like:

```sql
SELECT *
FROM Orders
WHERE customer_id = 1001
AND order_date >= '2025-01-01';
```

---

# 🔟 Full-Text Index

Optimized for text searching.

```sql
CREATE FULLTEXT INDEX idx_comments
ON Reviews(comment);
```

Example:

```sql
SELECT *
FROM Reviews
WHERE MATCH(comment)
AGAINST ('excellent');
```

---

# 1️⃣1️⃣ Creating and Managing Indexes

### Create Index

```sql
CREATE INDEX idx_customer_id
ON Orders(customer_id);
```

### Drop Index

```sql
DROP INDEX idx_customer_id;
```

---

# 1️⃣2️⃣ Query Optimization Basics

Query Optimization means:

> Retrieving data using the least amount of resources and time.

Goals:

✅ Faster Execution

✅ Reduced CPU Usage

✅ Reduced Memory Usage

✅ Better Scalability

---

# 1️⃣3️⃣ Understanding Query Execution Plans

Execution plans show how the database executes a query.

They reveal:

* Table Scans
* Index Scans
* Joins
* Sorting Operations

---

# 1️⃣4️⃣ Using EXPLAIN

```sql
EXPLAIN
SELECT *
FROM Orders
WHERE customer_id = 1001;
```

EXPLAIN helps identify performance bottlenecks.

---

# 1️⃣5️⃣ Common Query Performance Problems

### ❌ SELECT *

```sql
SELECT *
FROM Employees;
```

### ✅ Better

```sql
SELECT employee_name
FROM Employees;
```

---

### ❌ Missing Indexes

Queries become slow on large tables.

---

### ❌ Unnecessary Sorting

```sql
ORDER BY employee_name;
```

Sorting large datasets can be expensive.

---

# 1️⃣6️⃣ Optimizing WHERE Clauses

Avoid functions on indexed columns.

### Slow

```sql
SELECT *
FROM Orders
WHERE YEAR(order_date) = 2025;
```

### Optimized

```sql
SELECT *
FROM Orders
WHERE order_date >= '2025-01-01'
AND order_date < '2026-01-01';
```

---

# 1️⃣7️⃣ Optimizing JOIN Operations

Use indexed columns.

### Better Join

```sql
SELECT *
FROM Orders o
INNER JOIN Customers c
ON o.customer_id = c.customer_id;
```

Index:

```sql
CREATE INDEX idx_customer_id
ON Orders(customer_id);
```

---

# 1️⃣8️⃣ Optimizing ORDER BY and GROUP BY

Columns frequently used in:

```sql
ORDER BY
GROUP BY
```

should often be indexed.

Example:

```sql
CREATE INDEX idx_department
ON Employees(department);
```

---

# 1️⃣9️⃣ Indexing Best Practices

✅ Index columns used in WHERE clauses

✅ Index JOIN columns

✅ Index ORDER BY columns

✅ Use Composite Indexes when appropriate

✅ Monitor index usage regularly

✅ Remove unused indexes

---

# 2️⃣0️⃣ Common Mistakes

### ❌ Over-Indexing

Too many indexes slow down:

```sql
INSERT
UPDATE
DELETE
```

operations.

---

### ❌ Indexing Small Tables

Small tables often don't need indexes.

---

### ❌ Ignoring Execution Plans

Optimization should be based on evidence.

---

### ❌ Using SELECT *

Retrieves unnecessary data.

---

# 2️⃣1️⃣ Real-World Optimization Examples

## E-Commerce

Search products by category and price.

---

## Banking

Fast transaction lookups.

---

## HR Systems

Employee search and reporting.

---

## Healthcare

Patient record retrieval.

---

## Logistics

Shipment tracking systems.

---

# 📝 Practice Exercises

### Exercise 1

Create an index on customer_id in the Orders table.

### Exercise 2

Use EXPLAIN to analyze a query.

### Exercise 3

Compare query performance before and after indexing.

### Exercise 4

Create a Unique Index on email.

### Exercise 5

Create a Composite Index on customer_id and order_date.

### Exercise 6

Optimize a query filtering by year.

### Exercise 7

Analyze a JOIN query using EXPLAIN.

### Exercise 8

Create a Full-Text Index.

### Exercise 9

Identify unnecessary indexes.

### Exercise 10

Optimize a reporting query.

### Exercise 11

Optimize a GROUP BY query.

### Exercise 12

Optimize an ORDER BY query.

### Exercise 13

Analyze a slow-running query.

### Exercise 14

Compare clustered vs non-clustered indexes.

### Exercise 15

Design an indexing strategy for an e-commerce database.

---

# 🎯 Key Takeaways

✅ Indexes improve query performance.

✅ Indexes act like a book's table of contents.

✅ Primary Keys automatically create indexes.

✅ Composite indexes improve multi-column searches.

✅ EXPLAIN helps analyze query execution.

✅ Avoid SELECT * in production queries.

✅ Over-indexing can hurt performance.

✅ Query optimization is essential for scalable applications.

---

# 📖 Day 20 Summary

Today, you learned how indexes help databases retrieve data efficiently and how query optimization techniques improve performance.

You explored different types of indexes, execution plans, optimization strategies, and real-world performance tuning techniques used by database administrators, data engineers, and backend developers.

Understanding indexing and optimization is a critical skill for working with large-scale databases and production systems.

---

## 🚀 Coming Up Next: Day 21 – Transactions & Concurrency Control

Topics Covered:

* Transactions
* ACID Properties
* COMMIT
* ROLLBACK
* SAVEPOINT
* Isolation Levels
* Concurrency Control
* Deadlocks

## Progress Status:** Day 20 Completed ✅**

---

[PREVIOUS: DAY19-VIEWS AND MATERIALIZED VIEWS](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/d1ea31cc73f3716b628f471bf5a7e81bf0e20707/DAY19/DAY19-%20Views%20%26%20Materialized%20Views.md)👆\
[NEXT: DAY21-TRANSACTIONS AND CONCURRENCY CONTROL]()👇
