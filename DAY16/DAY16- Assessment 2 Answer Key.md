# ✅ 30 Days of SQL – Day 16 Assessment 2 Answer Key

This answer key contains solutions for all 30 questions from the Day 16 Assessment.

---

# Part A: MCQ Answers (15 Marks)

| Q No. | Answer                       |
| ----- | ---------------------------- |
| 1     | C – INNER JOIN               |
| 2     | A – UNION                    |
| 3     | B – CURRENT_DATE             |
| 4     | C – GROUP BY                 |
| 5     | C – AVG()                    |
| 6     | C – Removes duplicate values |
| 7     | C – VARIANCE()               |
| 8     | A – LEFT JOIN                |
| 9     | B – MEDIAN()                 |
| 10    | B – CASE                     |
| 11    | C – PERCENTILE_CONT()        |
| 12    | B – 20                       |
| 13    | C – HAVING                   |
| 14    | C – MEDIAN()                 |
| 15    | B – Nested Aggregation       |

---

# Part B: Practical SQL Solutions

## Question 16

Display Employee Name and Department Name using INNER JOIN.

```sql
SELECT
e.employee_name,
d.department_name
FROM Employees e
INNER JOIN Departments d
ON e.department_id = d.department_id;
```

---

## Question 17

Display all employees even if they do not belong to any department.

```sql
SELECT
e.employee_name,
d.department_name
FROM Employees e
LEFT JOIN Departments d
ON e.department_id = d.department_id;
```

---

## Question 18

Retrieve unique department names.

```sql
SELECT DISTINCT department_name
FROM Departments;
```

---

## Question 19

Display today's date.

```sql
SELECT CURRENT_DATE;
```

Alternative:

```sql
SELECT CURDATE();
```

(MySQL)

---

## Question 20

Find total number of employees.

```sql
SELECT COUNT(*)
AS total_employees
FROM Employees;
```

---

## Question 21

Find average salary for each department.

```sql
SELECT
department,
AVG(salary) AS average_salary
FROM Employees
GROUP BY department;
```

---

## Question 22

Display employees earning above average salary.

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

## Question 23

Find duplicate employee names.

```sql
SELECT
employee_name,
COUNT(*) AS occurrences
FROM Employees
GROUP BY employee_name
HAVING COUNT(*) > 1;
```

---

## Question 24

Generate monthly sales totals.

```sql
SELECT
MONTH(order_date) AS month,
SUM(sales_amount) AS revenue
FROM Orders
GROUP BY MONTH(order_date);
```

---

## Question 25

Find department with highest average salary.

```sql
SELECT
department,
AVG(salary) AS avg_salary
FROM Employees
GROUP BY department
ORDER BY avg_salary DESC
LIMIT 1;
```

---

# Hard Level Solutions

## Question 26

Create KPI Report.

```sql
SELECT
COUNT(*) AS total_employees,
AVG(salary) AS average_salary,
MAX(salary) AS highest_salary,
MIN(salary) AS lowest_salary
FROM Employees;
```

---

## Question 27

Calculate Variance and Standard Deviation.

```sql
SELECT
VARIANCE(salary) AS salary_variance,
STDDEV(salary) AS salary_stddev
FROM Employees;
```

---

## Question 28

Find Median Salary.

### Oracle

```sql
SELECT
MEDIAN(salary) AS median_salary
FROM Employees;
```

### PostgreSQL / SQL Server

```sql
SELECT
PERCENTILE_CONT(0.5)
WITHIN GROUP (ORDER BY salary)
AS median_salary
FROM Employees;
```

---

## Question 29

Find Top 10% Salaries.

```sql
SELECT *
FROM Employees
WHERE salary >=
(
SELECT
PERCENTILE_CONT(0.9)
WITHIN GROUP (ORDER BY salary)
FROM Employees
);
```

---

## Question 30

Build Sales Dashboard Query.

```sql
SELECT
SUM(order_amount) AS total_revenue,
COUNT(*) AS total_orders,
AVG(order_amount) AS average_order_value,
MAX(order_amount) AS highest_order_value,
MIN(order_amount) AS lowest_order_value
FROM Orders;
```

---

# 🏆 Score Interpretation

| Score    | Performance            |
| -------- | ---------------------- |
| 27 – 30  | Excellent ⭐            |
| 24 – 26  | Very Good ✅            |
| 20 – 23  | Good 👍                |
| 15 – 19  | Fair 📚                |
| Below 15 | Needs More Practice 🔄 |

---

# 🎯 Skills Tested

✅ INNER JOIN

✅ LEFT JOIN

✅ DISTINCT

✅ Date Functions

✅ Aggregate Functions

✅ GROUP BY

✅ HAVING

✅ Subqueries

✅ KPI Analysis

✅ Variance & Standard Deviation

✅ Median Calculations

✅ Percentiles

✅ Dashboard Reporting

---

# 📖 Assessment 2 Conclusion

If you were able to solve most of these questions confidently, you now have a strong understanding of:

* Relational Data Analysis
* Business Reporting
* SQL Aggregations
* KPI Development
* Analytical SQL

These concepts form the foundation of real-world Data Analytics, Business Intelligence, and Reporting Systems.

---

## 🚀 Next: Day 17 – Window Functions

Topics:

```sql
ROW_NUMBER()
RANK()
DENSE_RANK()
NTILE()
CUME_DIST()
LEAD()
LAG()
```

## Assessment 2 Completed Successfully ✅
---
[PREVIOUS: DAY16](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/7d5d25ff617f20193e8e39707028876433c4fb24/DAY16/DAY16%20-%20SQL%20Mastery%20Assessment%202.md)👆\
[NEXT: DAY17]()👇
