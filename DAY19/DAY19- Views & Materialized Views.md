# 🚀 30 Days of SQL – Day 19: Views & Materialized Views

Welcome to **Day 19** of the **30 Days of SQL Challenge**!

As databases grow larger, queries become longer and more repetitive. SQL provides a powerful feature called **Views** that helps simplify complex queries, improve security, and make database management easier.

Today, you'll learn how Views work, why they are important, and how organizations use them in real-world applications.

---

# 📚 Table of Contents

1. Introduction to Views
2. Why Do We Need Views?
3. How Views Work
4. Creating a View
5. Querying a View
6. Updating Data Through Views
7. Replacing a View
8. Dropping a View
9. Types of Views
10. Simple Views
11. Complex Views
12. Materialized Views
13. Views vs Tables
14. Views vs CTEs
15. Security Through Views
16. Real-World Business Use Cases
17. Common Mistakes
18. Practice Exercises
19. Key Takeaways
20. Day 19 Summary

---

# 1️⃣ Introduction to Views

A **View** is a virtual table created from the result of a SQL query.

Unlike a regular table, a View does not store data itself. Instead, it stores the SQL query used to generate the data.

Think of a View as:

```text
Table = Stores Data

View = Stores Query
```

---

# 2️⃣ Why Do We Need Views?

Suppose every day you need to run:

```sql
SELECT
e.employee_name,
d.department_name,
e.salary
FROM Employees e
INNER JOIN Departments d
ON e.department_id = d.department_id;
```

Instead of writing this query repeatedly, create a View once and use it forever.

Benefits:

✅ Simplifies complex queries

✅ Improves readability

✅ Enhances security

✅ Reduces duplicate code

✅ Makes reporting easier

---

# 3️⃣ How Views Work

### Base Tables

#### Employees

| Employee_ID | Employee_Name | Department_ID |
|------------|---------------|---------------|
| 1 | John | 101 |
| 2 | Mary | 102 |

#### Departments

| Department_ID | Department_Name |
|--------------|----------------|
| 101 | HR |
| 102 | IT |

---

### View Output

| Employee_Name | Department_Name |
|--------------|----------------|
| John | HR |
| Mary | IT |

The View pulls data from underlying tables whenever it is queried.

---

# 4️⃣ Creating a View

### Syntax

```sql
CREATE VIEW view_name AS
SELECT column1, column2
FROM table_name;
```

### Example

```sql
CREATE VIEW Employee_Departments AS
SELECT
e.employee_name,
d.department_name
FROM Employees e
INNER JOIN Departments d
ON e.department_id = d.department_id;
```

---

# 5️⃣ Querying a View

Once created, a View behaves like a table.

```sql
SELECT *
FROM Employee_Departments;
```

Output:

| Employee_Name | Department_Name |
|--------------|----------------|
| John | HR |
| Mary | IT |

---

# 6️⃣ Updating Data Through Views

Some Views allow updates.

### Example

```sql
UPDATE Employee_View
SET salary = 70000
WHERE employee_id = 1;
```

The underlying table gets updated.

---

### Note

Updates are only possible when:

✅ Single table involved

✅ No GROUP BY

✅ No Aggregate Functions

✅ No DISTINCT

---

# 7️⃣ Replacing a View

Modify an existing View.

### MySQL

```sql
CREATE OR REPLACE VIEW Employee_View AS
SELECT
employee_name,
salary
FROM Employees;
```

---

# 8️⃣ Dropping a View

Delete a View permanently.

```sql
DROP VIEW Employee_View;
```

Only the View is removed.

The original table remains unchanged.

---

# 9️⃣ Types of Views

There are two major categories:

### 1. Simple Views

Built from a single table.

### 2. Complex Views

Built using joins, aggregations, and multiple tables.

---

# 🔟 Simple Views

### Example

```sql
CREATE VIEW Employee_Basic AS
SELECT
employee_id,
employee_name,
salary
FROM Employees;
```

Advantages:

✅ Easy to create

✅ Usually updateable

---

# 1️⃣1️⃣ Complex Views

Uses:

- Multiple Tables
- JOINs
- Aggregate Functions
- GROUP BY

### Example

```sql
CREATE VIEW Department_Salary_Report AS
SELECT
department_id,
AVG(salary) AS average_salary
FROM Employees
GROUP BY department_id;
```

---

# 1️⃣2️⃣ Materialized Views

A Materialized View stores actual data physically.

Unlike regular Views:

| Regular View | Materialized View |
|-------------|------------------|
| Stores query | Stores data |
| Executes every time | Faster retrieval |
| Always current | Requires refresh |

---

### Example

```sql
CREATE MATERIALIZED VIEW Monthly_Sales AS
SELECT
month,
SUM(sales_amount) AS total_sales
FROM Sales
GROUP BY month;
```

---

### Refreshing Materialized Views

```sql
REFRESH MATERIALIZED VIEW Monthly_Sales;
```

---

# 1️⃣3️⃣ Views vs Tables

| Feature | Table | View |
|----------|--------|------|
| Stores Data | ✅ | ❌ |
| Occupies Storage | ✅ | Minimal |
| Updateable | ✅ | Sometimes |
| Query Reusability | ❌ | ✅ |

---

# 1️⃣4️⃣ Views vs CTEs

| Feature | View | CTE |
|----------|------|------|
| Permanent | ✅ | ❌ |
| Temporary | ❌ | ✅ |
| Reusable | ✅ | Within Query |
| Stored in Database | ✅ | ❌ |

---

# 1️⃣5️⃣ Security Through Views

One of the biggest advantages of Views is security.

Suppose Employees table contains:

| ID | Name | Salary | PAN_Number |
|----|------|---------|-----------|

HR should see everything.

Managers should only see:

| Name | Salary |

Create a View:

```sql
CREATE VIEW Manager_View AS
SELECT
employee_name,
salary
FROM Employees;
```

Managers never access sensitive columns.

---

# 1️⃣6️⃣ Real-World Business Use Cases

## Banking

Customer account summaries.

---

## E-Commerce

Sales dashboards.

---

## HR Systems

Employee reports.

---

## Healthcare

Patient appointment views.

---

## Education

Student performance reports.

---

## Manufacturing

Inventory reporting.

---

# 1️⃣7️⃣ Common Mistakes

### ❌ Using Views for Everything

Views simplify queries but may reduce performance if nested excessively.

---

### ❌ Forgetting Permissions

Users need access rights to query Views.

---

### ❌ Expecting All Views to be Updateable

Complex Views often cannot be updated.

---

### ❌ Ignoring Materialized View Refreshes

Stored data can become outdated.

---

# 📝 Practice Exercises

### Exercise 1

Create a View displaying employee names and salaries.

---

### Exercise 2

Create a View for employees in the HR department.

---

### Exercise 3

Query data from a View.

---

### Exercise 4

Modify an existing View.

---

### Exercise 5

Drop a View.

---

### Exercise 6

Create a View using an INNER JOIN.

---

### Exercise 7

Create a View using a LEFT JOIN.

---

### Exercise 8

Build a Department Salary Report View.

---

### Exercise 9

Create a Customer Orders View.

---

### Exercise 10

Create a Student Performance View.

---

### Exercise 11

Create a Product Sales View.

---

### Exercise 12

Create a Materialized View.

---

### Exercise 13

Refresh a Materialized View.

---

### Exercise 14

Build a secure Manager View.

---

### Exercise 15

Design a complete Business Dashboard View.

---

# 🎯 Key Takeaways

✅ Views are virtual tables.

✅ Views store queries, not data.

✅ Views simplify complex SQL statements.

✅ Views improve security.

✅ Views reduce code duplication.

✅ Simple Views are often updateable.

✅ Complex Views may not be updateable.

✅ Materialized Views store actual data.

✅ Materialized Views improve performance.

✅ Views are heavily used in reporting and dashboard development.

---

# 📖 Day 19 Summary

Today, you learned how Views help simplify SQL development by storing reusable queries as virtual tables.

You explored:

- Creating Views
- Updating Views
- Dropping Views
- Materialized Views
- Security Benefits
- Business Reporting Applications

Views are widely used in enterprise systems because they improve maintainability, security, and reporting efficiency.

---

## 🚀 Coming Up Next: Day 20 – Assessment 3 (Days 11–19)

Topics Covered:

- Joins
- Set Operations
- Date Functions
- EDA
- Advanced Aggregations
- Window Functions
- CTEs
- Views

## Progress Status: Day 19 Completed ✅

---

[PREVIOUS: DAY18-WINDOWS FUNCTIONS](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/753baeb49922466534a4c8d34cd4d09116cf0b15/DAY18/DAY18-%20Common%20Table%20Expressions%20(CTEs)%20%26%20Recursive%20CTEs.md)👆\
[NEXT: DAY20-INDEXES AND OPTIMIZATIONS]()👇
