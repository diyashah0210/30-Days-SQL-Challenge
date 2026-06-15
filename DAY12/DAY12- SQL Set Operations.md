# 🚀 30 Days of SQL – Day 12: SQL Set Operations

Welcome to **Day 12** of the **30 Days of SQL Challenge**!

In Day 11, we learned how **Joins** combine data from multiple tables horizontally (column-wise). Today, we'll explore **Set Operations**, which combine the results of multiple queries vertically (row-wise).

Set Operations are widely used in reporting, analytics, auditing, and data consolidation tasks.

---

# 📚 Table of Contents

1. Introduction to Set Operations
2. Why Do We Need Set Operations?
3. Joins vs Set Operations
4. Rules for Set Operations
5. UNION
6. UNION ALL
7. INTERSECT
8. EXCEPT / MINUS
9. Comparing All Set Operators
10. Set Operator Execution Flow
11. Real-World Applications
12. Performance Considerations
13. Common Mistakes
14. Practice Exercises
15. Key Takeaways
16. Day 12 Summary

---

# 1️⃣ Introduction to Set Operations

Set Operations are SQL operators used to combine the results of two or more `SELECT` statements into a single result set.

Unlike Joins, which combine columns from multiple tables, Set Operations combine rows from multiple query results.

### Example

Table A

| City |
|--------|
| Mumbai |
| Delhi |

Table B

| City |
|--------|
| Pune |
| Ahmedabad |

Combined Result

| City |
|--------|
| Mumbai |
| Delhi |
| Pune |
| Ahmedabad |

---

# 2️⃣ Why Do We Need Set Operations?

Imagine an e-commerce company storing orders from two different channels.

### Online Orders

| order_id |
|-----------|
| 101 |
| 102 |
| 103 |

### Store Orders

| order_id |
|-----------|
| 104 |
| 105 |
| 106 |

Management wants a single list containing all orders.

This is where Set Operations become useful.

---

# 3️⃣ Joins vs Set Operations

| Feature | JOIN | SET OPERATIONS |
|----------|--------|---------------|
| Combines | Columns | Rows |
| Works On | Related Tables | Query Results |
| Uses Keys | Yes | No |
| Direction | Horizontal | Vertical |

### JOIN

```sql
Customers + Orders
```

Produces:

```text
Customer Name | Order Amount
```

### UNION

```sql
Customers
UNION
Suppliers
```

Produces:

```text
One Combined List
```

---

# 4️⃣ Rules for Set Operations

Before using Set Operators, the following rules must be followed:

## Rule 1: Same Number of Columns

✅ Valid

```sql
SELECT id, name
FROM Employees

UNION

SELECT id, name
FROM Customers;
```

❌ Invalid

```sql
SELECT id, name

UNION

SELECT id;
```

---

## Rule 2: Compatible Datatypes

Corresponding columns should contain compatible datatypes.

### Examples

✅ INT ↔ INT

✅ VARCHAR ↔ VARCHAR

❌ INT ↔ DATE

---

## Rule 3: Column Names

The final output column names are taken from the first SELECT statement.

---

# 5️⃣ UNION

The `UNION` operator combines results from multiple queries and automatically removes duplicate rows.

## Syntax

```sql
SELECT column_name
FROM table1

UNION

SELECT column_name
FROM table2;
```

### Example

Customers

| City |
|--------|
| Mumbai |
| Delhi |
| Pune |

Suppliers

| City |
|--------|
| Pune |
| Delhi |
| Ahmedabad |

```sql
SELECT city
FROM Customers

UNION

SELECT city
FROM Suppliers;
```

### Result

| City |
|--------|
| Mumbai |
| Delhi |
| Pune |
| Ahmedabad |

Duplicates are removed automatically.

---

# 6️⃣ UNION ALL

The `UNION ALL` operator combines results but retains duplicate values.

## Syntax

```sql
SELECT column_name
FROM table1

UNION ALL

SELECT column_name
FROM table2;
```

### Result

| City |
|--------|
| Mumbai |
| Delhi |
| Pune |
| Pune |
| Delhi |
| Ahmedabad |

Duplicates are preserved.

### When to Use UNION ALL?

- When duplicates are meaningful.
- When performance is important.
- When combining transactional datasets.

---

# 7️⃣ INTERSECT

The `INTERSECT` operator returns only the records that exist in both result sets.

## Syntax

```sql
SELECT city
FROM Customers

INTERSECT

SELECT city
FROM Suppliers;
```

### Result

| City |
|--------|
| Delhi |
| Pune |

Only common values appear.

---

# 8️⃣ EXCEPT / MINUS

Returns rows from the first query that are not present in the second query.

## Syntax

```sql
SELECT city
FROM Customers

EXCEPT

SELECT city
FROM Suppliers;
```

### Result

| City |
|--------|
| Mumbai |

### Database Compatibility

| Database | Operator |
|------------|----------|
| SQL Server | EXCEPT |
| PostgreSQL | EXCEPT |
| Oracle | MINUS |

---

# 9️⃣ Comparing All Set Operators

| Operator | Removes Duplicates | Returns |
|------------|-------------------|----------|
| UNION | ✅ Yes | Combined Rows |
| UNION ALL | ❌ No | Combined Rows |
| INTERSECT | ✅ Yes | Common Rows |
| EXCEPT | ✅ Yes | Unique Rows from First Query |

---

# 🔟 Set Operator Execution Flow

## UNION

```text
Query 1
   +
Query 2
   ↓
Remove Duplicates
   ↓
Final Result
```

## UNION ALL

```text
Query 1
   +
Query 2
   ↓
Final Result
```

No duplicate checking is performed.

---

# 1️⃣1️⃣ Real-World Applications

## E-Commerce

```text
Online Orders
UNION
Store Orders
```

---

## Banking

```text
Savings Accounts
UNION
Current Accounts
```

---

## Education

```text
Current Students
UNION
Alumni
```

---

## Healthcare

```text
Current Patients
UNION
Past Patients
```

---

## HR Systems

```text
Current Employees
UNION
Former Employees
```

---

# 1️⃣2️⃣ Performance Considerations

## UNION

- Removes duplicates.
- Requires additional processing.
- Slightly slower.

## UNION ALL

- Does not remove duplicates.
- Faster execution.
- Preferred when duplicate elimination is not required.

---

# 1️⃣3️⃣ Common Mistakes

## Different Number of Columns

❌

```sql
SELECT id, name
UNION
SELECT id;
```

---

## Incompatible Datatypes

❌

```sql
SELECT employee_id
UNION
SELECT joining_date;
```

---

## Using UNION Instead of UNION ALL

Sometimes duplicate records are important and should not be removed.

---

# 📝 Practice Exercises

## Exercise 1

Create two tables:

### CurrentEmployees

| employee_id | employee_name |
|------------|---------------|

### FormerEmployees

| employee_id | employee_name |
|------------|---------------|

Combine both tables using `UNION`.

---

## Exercise 2

Repeat Exercise 1 using `UNION ALL`.

Observe the difference in output.

---

## Exercise 3

Create two tables containing city names and find common cities using `INTERSECT`.

---

## Exercise 4

Find cities present in Customers but not in Suppliers using `EXCEPT`.

---

## Exercise 5

Create two product tables and identify products available in both stores.

---

## Exercise 6

Create two product tables and identify products available only in Store A.

---

## Exercise 7

Create OnlineOrders and StoreOrders tables.

Write queries to:

- Display all orders using UNION.
- Display all orders using UNION ALL.
- Find common orders.
- Find online-only orders.

---

## Exercise 8

Create two student lists:

- Current Students
- Alumni

Combine both datasets using appropriate Set Operators and compare the outputs.

---

# 🎯 Key Takeaways

✅ Set Operations combine rows from multiple query results.

✅ UNION removes duplicate rows.

✅ UNION ALL keeps duplicate rows.

✅ INTERSECT returns common records.

✅ EXCEPT/MINUS returns records unique to the first query.

✅ Both queries must return the same number of columns.

✅ Corresponding columns should have compatible datatypes.

✅ UNION ALL generally performs faster than UNION.

<img width="647" height="433" alt="image" src="https://github.com/user-attachments/assets/55dad5da-7b45-4ed2-8f56-0358e54c2ddb" />

---

# 📖 Day 12 Summary

Today, you learned how SQL Set Operations help combine results from multiple queries into a single output. While Joins connect tables horizontally, Set Operators merge datasets vertically, making them extremely useful for reporting, analytics, data migration, auditing, and business intelligence tasks.

Understanding when to use UNION, UNION ALL, INTERSECT, and EXCEPT is a fundamental skill for every SQL developer and data analyst.

---

## 🚀 Coming Up Next: Day 13 – Date, Time & String Functions

You'll learn:

```sql
NOW()
CURDATE()
CURRENT_TIMESTAMP
DATEDIFF()
DATEADD()
```

and discover how SQL handles and manipulates dates, times, and text data efficiently.

## Progress Status: Day 12 Completed ✅
---

[PREVIOUS: DAY11](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/fc7895c06a0591070484f5235a55808a4dae69ea/DAY11/DAY11-%20SQL%20Joins%20Fundamentals.md) 👆/
[NEXT: DAY13]()👇
