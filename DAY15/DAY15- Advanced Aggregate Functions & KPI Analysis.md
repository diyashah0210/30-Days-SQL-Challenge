# 🚀 30 Days of SQL – Day 15: Advanced Aggregate Functions & KPI Analysis

Welcome to **Day 15** of the **30 Days of SQL Challenge**!

Until now, we've learned how to retrieve, filter, sort, join, and analyze data. Today, we'll explore advanced aggregate functions and understand how organizations use them to measure business performance through Key Performance Indicators (KPIs).

Aggregate functions help transform raw data into meaningful insights that support business decision-making.

---

# 📚 Table of Contents

1. Introduction to Aggregate Functions
2. Why Are Aggregate Functions Important?
3. Advanced Aggregate Functions Overview
4. VARIANCE()
5. STDDEV()
6. MEDIAN()
7. PERCENTILE_CONT()
8. PERCENTILE_DISC()
9. Conditional Aggregation
10. Nested Aggregation
11. KPI Analysis
12. Revenue Analysis
13. Profit Analysis
14. Department-wise Analytics
15. Sales Performance Dashboard Queries
16. Common Mistakes
17. Practice Exercises
18. Key Takeaways
19. Day 15 Summary

---

# 1️⃣ Introduction to Aggregate Functions

Aggregate Functions perform calculations on multiple rows and return a single summarized result.

Instead of examining thousands of records individually, aggregate functions allow us to answer questions such as:

* What is the average salary?
* What is the total revenue?
* How much variation exists in sales?
* What is the median transaction amount?

These functions are widely used in:

* Business Intelligence
* Data Analytics
* Reporting Systems
* Dashboard Development
* Financial Analysis

---

# 2️⃣ Why Are Aggregate Functions Important?

Businesses rely on aggregate functions every day.

Examples:

| Business Area | Usage                        |
| ------------- | ---------------------------- |
| Sales         | Revenue Analysis             |
| Finance       | Profit Calculation           |
| HR            | Salary Analysis              |
| Banking       | Transaction Analysis         |
| Education     | Student Performance Analysis |

Aggregate functions help identify:

* Trends
* Performance
* Variability
* Outliers
* Business Opportunities

---

# 3️⃣ Advanced Aggregate Functions Overview

| Function          | Description                             |
| ----------------- | --------------------------------------- |
| VARIANCE()        | Calculates variance of a numeric column |
| STDDEV()          | Calculates standard deviation           |
| MEDIAN()          | Finds the middle value                  |
| PERCENTILE_CONT() | Returns continuous percentile           |
| PERCENTILE_DISC() | Returns discrete percentile             |

---

# 4️⃣ VARIANCE()

Variance measures how far values are spread from the average.

### Syntax

```sql
SELECT VARIANCE(column_name)
FROM table_name;
```

### Example

```sql
SELECT VARIANCE(salary)
AS salary_variance
FROM Employees;
```

### Business Use

Determine salary consistency across employees.

Higher variance indicates larger salary differences.

---

# 5️⃣ STDDEV()

Standard Deviation measures data spread around the average.

### Syntax

```sql
SELECT STDDEV(column_name)
FROM table_name;
```

### Example

```sql
SELECT STDDEV(salary)
AS salary_stddev
FROM Employees;
```

### Business Use

Identify consistency in:

* Salaries
* Sales
* Bonuses
* Revenue

---

# 6️⃣ MEDIAN()

Median represents the middle value of a dataset.

Unlike averages, median is not heavily affected by outliers.

### Example

```sql
SELECT MEDIAN(salary)
AS median_salary
FROM Employees;
```

### Example Dataset

| Salary |
| ------ |
| 30000  |
| 35000  |
| 40000  |
| 45000  |
| 500000 |

### Result

Median = 40000

Average = 131000

Median provides a more realistic picture.

---

# 7️⃣ PERCENTILE_CONT()

Returns a continuous percentile.

### Example

Find the 90th percentile salary.

```sql
SELECT
PERCENTILE_CONT(0.90)
WITHIN GROUP (ORDER BY salary)
AS top_salary_threshold
FROM Employees;
```

### Use Cases

* Top 10% earners
* Top-performing salespeople
* Premium customers

---

# 8️⃣ PERCENTILE_DISC()

Returns an actual value from the dataset.

### Example

```sql
SELECT
PERCENTILE_DISC(0.75)
WITHIN GROUP (ORDER BY salary)
AS percentile_salary
FROM Employees;
```

### Difference

| Function          | Returns          |
| ----------------- | ---------------- |
| PERCENTILE_CONT() | Calculated Value |
| PERCENTILE_DISC() | Existing Value   |

---

# 9️⃣ Conditional Aggregation

Conditional Aggregation applies aggregate functions only when conditions are satisfied.

### Example

Count employees earning more than ₹100,000.

```sql
SELECT
COUNT(
CASE
WHEN salary > 100000
THEN 1
END
) AS high_salary_count
FROM Employees;
```

---

### Revenue by Category

```sql
SELECT
SUM(
CASE
WHEN category = 'Electronics'
THEN sales_amount
ELSE 0
END
) AS electronics_revenue
FROM Sales;
```

---

# 🔟 Nested Aggregation

Aggregation performed inside another query.

### Example

Find department with highest average salary.

```sql
SELECT *
FROM
(
    SELECT department,
           AVG(salary) AS avg_salary
    FROM Employees
    GROUP BY department
) AS department_salary
ORDER BY avg_salary DESC;
```

---

# 1️⃣1️⃣ KPI Analysis

KPI stands for Key Performance Indicator.

KPIs help organizations measure performance.

### Common KPIs

| Industry   | KPI            |
| ---------- | -------------- |
| Sales      | Revenue        |
| Banking    | Loan Volume    |
| HR         | Employee Count |
| Education  | Enrollment     |
| E-Commerce | Orders         |

---

# 1️⃣2️⃣ Revenue Analysis

### Total Revenue

```sql
SELECT SUM(sales_amount)
AS total_revenue
FROM Sales;
```

---

### Revenue by Month

```sql
SELECT
MONTH(order_date),
SUM(sales_amount)
FROM Sales
GROUP BY MONTH(order_date);
```

---

### Revenue by City

```sql
SELECT city,
       SUM(sales_amount)
FROM Sales
GROUP BY city;
```

---

# 1️⃣3️⃣ Profit Analysis

Profit Formula:

```text
Profit = Revenue - Cost
```

### Example

```sql
SELECT
SUM(revenue) - SUM(cost)
AS total_profit
FROM Sales;
```

---

### Profit by Product

```sql
SELECT
product_name,
SUM(revenue - cost)
AS profit
FROM Sales
GROUP BY product_name;
```

---

# 1️⃣4️⃣ Department-wise Analytics

### Employee Count by Department

```sql
SELECT department,
COUNT(*)
FROM Employees
GROUP BY department;
```

---

### Average Salary by Department

```sql
SELECT department,
AVG(salary)
FROM Employees
GROUP BY department;
```

---

### Maximum Salary by Department

```sql
SELECT department,
MAX(salary)
FROM Employees
GROUP BY department;
```

---

# 1️⃣5️⃣ Sales Performance Dashboard Queries

### Top Selling Products

```sql
SELECT
product_name,
COUNT(*)
FROM Orders
GROUP BY product_name
ORDER BY COUNT(*) DESC;
```

---

### Top Revenue Cities

```sql
SELECT
city,
SUM(sales_amount)
FROM Sales
GROUP BY city
ORDER BY SUM(sales_amount) DESC;
```

---

### Monthly Revenue Trend

```sql
SELECT
MONTH(order_date),
SUM(sales_amount)
FROM Sales
GROUP BY MONTH(order_date);
```

---

### Customer Purchase Frequency

```sql
SELECT
customer_id,
COUNT(*)
FROM Orders
GROUP BY customer_id;
```

---

# 1️⃣6️⃣ Common Mistakes

### ❌ Using AVG Instead of MEDIAN

Outliers can distort averages.

---

### ❌ Ignoring Variance

Average alone does not show data spread.

---

### ❌ Missing GROUP BY

```sql
SELECT department,
AVG(salary)
FROM Employees;
```

Invalid in most databases.

---

### ❌ Incorrect Conditional Aggregation

Always include ELSE 0 where appropriate.

---

# 📝 Practice Exercises

## Exercise 1

Calculate variance of employee salaries.

---

## Exercise 2

Calculate standard deviation of salaries.

---

## Exercise 3

Find median salary.

---

## Exercise 4

Find the 75th percentile of salaries.

---

## Exercise 5

Find the 90th percentile of sales.

---

## Exercise 6

Count employees earning more than ₹100,000.

---

## Exercise 7

Calculate revenue generated by each product category.

---

## Exercise 8

Find department with highest average salary.

---

## Exercise 9

Calculate total company revenue.

---

## Exercise 10

Calculate total company profit.

---

## Exercise 11

Generate monthly revenue reports.

---

## Exercise 12

Find top-performing cities based on sales.

---

## Exercise 13

Create three KPIs for HR Analytics.

---

## Exercise 14

Create three KPIs for Sales Analytics.

---

## Exercise 15

Build a mini dashboard containing:

* Total Revenue
* Total Profit
* Average Salary
* Highest Salary
* Employee Count

---

# 🎯 Key Takeaways

✅ Aggregate functions summarize large datasets.

✅ VARIANCE() measures data spread.

✅ STDDEV() measures consistency.

✅ MEDIAN() provides a robust middle value.

✅ PERCENTILE_CONT() calculates continuous percentiles.

✅ PERCENTILE_DISC() returns actual percentile values.

✅ Conditional Aggregation enables KPI calculations.

✅ Nested Aggregation supports advanced analytics.

✅ Aggregate Functions power dashboards and business reports.

---

# 📖 Day 15 Summary

Today, you learned advanced aggregate functions and their role in business analytics. You explored variance, standard deviation, median calculations, percentile analysis, conditional aggregation, nested aggregation, KPI reporting, revenue analysis, profit calculations, and dashboard reporting techniques.

These concepts are widely used in Business Intelligence, Data Analytics, Financial Reporting, HR Analytics, and Enterprise Dashboard Development.

---

## 🚀 Coming Up Next: Day 16 – SQL Assessment 2

Topics Covered:

* Joins
* Set Operations
* Date Functions
* EDA
* Aggregate Functions
* KPI Analysis

## Progress Status: Day 15 Completed ✅
---
[PREVIOUS: DAY14](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/29dd083d419622f472cc60eb0bf5602811e76997/DAY14/DAY14-%20Exploratory%20Data%20Analysis%20(EDA)%20Using%20SQL.md)👆\
[NEXT: DAY16]()👇
