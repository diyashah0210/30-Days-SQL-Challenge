# 🚀 30 Days of SQL – Day 9: GROUP BY, HAVING & Subqueries

Welcome to **Day 9** of the **30 Days of SQL Challenge**!

In Day 8, you learned how to use SQL Functions such as:

- COUNT()
- SUM()
- AVG()
- MIN()
- MAX()
- UPPER()
- LOWER()
- CONCAT()

While aggregate functions help summarize data, they become even more powerful when combined with **GROUP BY** and **HAVING** clauses.

Today, you'll learn how to:

- Group records into categories
- Generate department-wise reports
- Filter grouped data
- Write nested queries using Subqueries

These concepts are heavily used in reporting, business intelligence, dashboards, and analytics.

---

# 📚 Table of Contents

1. Why Grouping Data is Important

2. Understanding GROUP BY

3. Multiple Column Grouping

4. Understanding HAVING Clause

5. WHERE vs HAVING

6. Combining GROUP BY and HAVING

7. Understanding Subqueries

8. Types of Subqueries

9. Single Row Subqueries

10. Multi-Row Subqueries

11. Subqueries with IN

12. Subqueries with Aggregate Functions

13. Practice Exercises

14. Key Takeaways

15. Day 9 Summary

---

# 1️⃣ Why Grouping Data is Important

Imagine a company with 10,000 employees.

Management wants answers to questions like:

- How many employees work in each department?
- What is the average salary in each department?
- Which department has the highest salary expense?

Instead of manually calculating this information, SQL allows us to group data automatically.

---

# 📖 Library Analogy

Imagine a library containing thousands of books.

Without grouping:

```text
All books appear together.
```

With grouping:

```text
Science Books
Mathematics Books
Technology Books
History Books
```

Grouping helps organize data into meaningful categories.

---

# 2️⃣ Understanding GROUP BY

The **GROUP BY** clause groups rows having the same values into summary groups.

## Syntax

```sql
SELECT column_name,
       aggregate_function(column_name)
FROM table_name
GROUP BY column_name;
```

---

## Sample Employees Table

| employee_id | employee_name | department | salary |
|------------|---------------|------------|---------|
| 1 | John | HR | 50000 |
| 2 | Sarah | IT | 70000 |
| 3 | Mike | HR | 60000 |
| 4 | David | IT | 80000 |

---

## GROUP BY with COUNT()

Find the number of employees in each department.

```sql
SELECT department,
       COUNT(*) AS total_employees
FROM Employees
GROUP BY department;
```

### Output

| department | total_employees |
|------------|----------------|
| HR | 2 |
| IT | 2 |

---

## GROUP BY with SUM()

Calculate total salary by department.

```sql
SELECT department,
       SUM(salary) AS total_salary
FROM Employees
GROUP BY department;
```

### Output

| department | total_salary |
|------------|-------------|
| HR | 110000 |
| IT | 150000 |

---

## GROUP BY with AVG()

Calculate average salary by department.

```sql
SELECT department,
       AVG(salary) AS average_salary
FROM Employees
GROUP BY department;
```

---

## GROUP BY with MIN() and MAX()

Find lowest and highest salaries in each department.

```sql
SELECT department,
       MIN(salary) AS lowest_salary,
       MAX(salary) AS highest_salary
FROM Employees
GROUP BY department;
```

---

# 3️⃣ Multiple Column Grouping

SQL allows grouping using multiple columns.

## Example

```sql
SELECT department,
       city,
       COUNT(*) AS employees
FROM Employees
GROUP BY department, city;
```

### Output

| department | city | employees |
|------------|------|-----------|
| HR | Mumbai | 5 |
| HR | Pune | 3 |
| IT | Mumbai | 7 |

---

# 4️⃣ Understanding HAVING Clause

The **HAVING** clause filters grouped data.

Think of it as:

```text
WHERE filters rows
HAVING filters groups
```

---

## Syntax

```sql
SELECT column_name,
       aggregate_function(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

---

# 5️⃣ WHERE vs HAVING

| WHERE | HAVING |
|---------|---------|
| Filters rows | Filters groups |
| Executes before GROUP BY | Executes after GROUP BY |
| Cannot use aggregate functions directly | Can use aggregate functions |

---

## WHERE Example

```sql
SELECT *
FROM Employees
WHERE salary > 50000;
```

Filters individual employees.

---

## HAVING Example

```sql
SELECT department,
       COUNT(*)
FROM Employees
GROUP BY department
HAVING COUNT(*) > 5;
```

Filters departments.

---

# 6️⃣ Combining GROUP BY and HAVING

Find departments with average salary greater than ₹60,000.

```sql
SELECT department,
       AVG(salary)
FROM Employees
GROUP BY department
HAVING AVG(salary) > 60000;
```

---

## Query Execution Order

```text
1. FROM
2. WHERE
3. GROUP BY
4. HAVING
5. SELECT
6. ORDER BY
```

---


# 7️⃣ Understanding Subqueries

A **Subquery** is a query written inside another query.

It is also called:

```text
Nested Query
Inner Query
```

---

## Basic Structure

```sql
SELECT column_name
FROM table_name
WHERE column_name =
(
    SELECT column_name
    FROM another_table
);
```

---

# 📖 Real-Life Analogy

Imagine asking:

```text
Who earns more than the average salary?
```

Step 1:

Find average salary.

Step 2:

Compare every employee salary against that value.

This is exactly what a subquery does.

---

# 8️⃣ Types of Subqueries

### 1. Single Row Subquery

Returns one value.

---

### 2. Multi-Row Subquery

Returns multiple values.

---

### 3. Correlated Subquery

Depends on the outer query.

(Advanced topic—covered later.)

---

# 9️⃣ Single Row Subqueries

Find employees earning more than average salary.

```sql
SELECT *
FROM Employees
WHERE salary >
(
    SELECT AVG(salary)
    FROM Employees
);
```

---

### Step 1

```sql
SELECT AVG(salary)
FROM Employees;
```

Output:

```text
65000
```

---

### Step 2

```sql
SELECT *
FROM Employees
WHERE salary > 65000;
```

Returns employees earning above average salary.

---

# 🔟 Multi-Row Subqueries

Returns multiple values.

## Example

Find employees working in departments located in Mumbai.

```sql
SELECT *
FROM Employees
WHERE department_id IN
(
    SELECT department_id
    FROM Departments
    WHERE city = 'Mumbai'
);
```

---


# 1️⃣1️⃣ Subqueries with IN

The IN operator is commonly used with subqueries.

```sql
SELECT *
FROM Students
WHERE course_id IN
(
    SELECT course_id
    FROM Courses
    WHERE duration > 6
);
```

---


# 1️⃣2️⃣ Subqueries with Aggregate Functions

Find employees earning maximum salary.

```sql
SELECT *
FROM Employees
WHERE salary =
(
    SELECT MAX(salary)
    FROM Employees
);
```

---

Find employees earning minimum salary.

```sql
SELECT *
FROM Employees
WHERE salary =
(
    SELECT MIN(salary)
    FROM Employees
);
```

---
# 1️⃣3️⃣📝 Practice Exercises

### Exercise 1

Display total employees in each department.

---

### Exercise 2

Display total salary by department.

---

### Exercise 3

Display average salary by department.

---

### Exercise 4

Display departments having more than 5 employees.

---

### Exercise 5

Display departments with average salary greater than ₹50,000.

---

### Exercise 6

Find employees earning above average salary.

---

### Exercise 7

Find employees earning maximum salary.

---

### Exercise 8

Find employees earning minimum salary.

---

### Exercise 9

Use a subquery with IN.

---

# 🎯 Key Takeaways

✅ Learned GROUP BY

✅ Grouped records using aggregate functions

✅ Used COUNT(), SUM(), AVG(), MIN(), MAX()

✅ Understood HAVING clause

✅ Learned WHERE vs HAVING

✅ Combined GROUP BY and HAVING

✅ Understood Subqueries

✅ Learned Single Row Subqueries

✅ Learned Multi-Row Subqueries

✅ Used Aggregate Functions inside Subqueries

---

# 📖 Day 9 Summary

Today, you learned how to organize data into meaningful groups using GROUP BY and how to filter those groups using HAVING. You also explored Subqueries, one of SQL's most powerful features, allowing queries to be nested inside other queries.

These concepts are widely used in reporting systems, dashboards, business intelligence platforms, and data analytics.

---

## 🚀 Coming Up Next: Day 10 – SQL Joins

You'll learn:

```sql
INNER JOIN
LEFT JOIN
RIGHT JOIN
FULL OUTER JOIN
SELF JOIN
CROSS JOIN
```

and understand how SQL combines data from multiple related tables.

## Progress Status: Day 9 Completed ✅
---
[PREVIOUS: DAY8]()
[NEXT: DAY10]()
