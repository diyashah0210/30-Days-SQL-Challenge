# 🚀 30 Days of SQL – Day 17: Window Functions

Welcome to **Day 17** of the **30 Days of SQL Challenge**!

Today, you'll learn one of the most powerful SQL concepts used in Data Analytics, Business Intelligence, Reporting, and SQL Interviews — **Window Functions**.

Unlike Aggregate Functions that collapse rows into groups, Window Functions perform calculations across related rows while preserving the original dataset.

---

# 📚 Table of Contents

1. Introduction to Window Functions
2. Why Do We Need Window Functions?
3. Aggregate Functions vs Window Functions
4. Understanding OVER()
5. Understanding PARTITION BY
6. Understanding ORDER BY in Window Functions
7. ROW_NUMBER()
8. RANK()
9. DENSE_RANK()
10. NTILE()
11. CUME_DIST()
12. LEAD()
13. LAG()
14. FIRST_VALUE()
15. LAST_VALUE()
16. Running Totals
17. Moving Averages
18. Real-World Business Use Cases
19. Common Mistakes
20. Practice Exercises
21. Key Takeaways
22. Day 17 Summary

---

# 1️⃣ Introduction to Window Functions

Window Functions perform calculations across a set of rows related to the current row while keeping every row visible in the output.

Unlike `GROUP BY`, Window Functions:

✅ Preserve row-level data

✅ Perform ranking

✅ Compare records

✅ Calculate running totals

✅ Analyze trends

---

# 2️⃣ Why Do We Need Window Functions?

Consider the following Employee table:

| Employee | Department | Salary |
|-----------|------------|---------|
| John | HR | 50000 |
| Mary | HR | 60000 |
| Alex | IT | 70000 |
| David | IT | 90000 |

Suppose we want to:

- Rank employees by salary
- Compare salaries within departments
- Find previous and next salaries
- Calculate running totals

Traditional Aggregate Functions cannot perform these tasks effectively.

Window Functions solve these problems.

---

# 3️⃣ Aggregate Functions vs Window Functions

| Aggregate Functions | Window Functions |
|---------------------|------------------|
| Collapse rows | Keep rows |
| Return one result per group | Return one result per row |
| Use GROUP BY | Use OVER() |
| SUM(), AVG(), COUNT() | ROW_NUMBER(), RANK(), LEAD() |

<img width="764" height="200" alt="image" src="https://github.com/user-attachments/assets/65688148-7951-49ea-a480-ae8a299adf41" />

---

# 4️⃣ Understanding OVER()

Every Window Function uses the `OVER()` clause.

### Syntax

```sql
SELECT
column_name,
WINDOW_FUNCTION()
OVER()
FROM table_name;
```

The `OVER()` clause defines the set of rows used for the calculation.

---

# 5️⃣ Understanding PARTITION BY

`PARTITION BY` divides data into logical groups while keeping all rows visible.

### Example

```sql
SELECT
employee_name,
department,
salary,
AVG(salary)
OVER(PARTITION BY department) AS department_average
FROM Employees;
```

### Output

| Employee | Department | Salary | Department Average |
|-----------|------------|---------|-------------------|
| John | HR | 50000 | 55000 |
| Mary | HR | 60000 | 55000 |
| Alex | IT | 70000 | 80000 |
| David | IT | 90000 | 80000 |

---

# 6️⃣ Understanding ORDER BY in Window Functions

`ORDER BY` determines the sequence of calculations.

### Example

```sql
SELECT
employee_name,
salary,
ROW_NUMBER()
OVER(ORDER BY salary DESC) AS row_num
FROM Employees;
```

---
# 7️⃣ ROW_NUMBER()

Assigns a unique sequential number to each row.

### Example

```sql
SELECT
employee_name,
salary,
ROW_NUMBER()
OVER(ORDER BY salary DESC) AS row_number
FROM Employees;
```

### Output

| Employee | Salary | Row Number |
|-----------|---------|------------|
| David | 90000 | 1 |
| Alex | 70000 | 2 |
| Mary | 60000 | 3 |
| John | 50000 | 4 |

---

# 8️⃣ RANK()

Assigns ranks and skips numbers when ties occur.

### Example

```sql
SELECT
employee_name,
salary,
RANK()
OVER(ORDER BY salary DESC) AS salary_rank
FROM Employees;
```

### Example Result

| Salary | Rank |
|---------|------|
| 90000 | 1 |
| 90000 | 1 |
| 70000 | 3 |

Notice Rank 2 is skipped.

---

# 9️⃣ DENSE_RANK()

Assigns ranks without skipping numbers.

### Example

```sql
SELECT
employee_name,
salary,
DENSE_RANK()
OVER(ORDER BY salary DESC) AS dense_rank
FROM Employees;
```

### Example Result

| Salary | Dense Rank |
|---------|------------|
| 90000 | 1 |
| 90000 | 1 |
| 70000 | 2 |

# COMBINED EXAMPLE: 
<img width="532" height="200" alt="image" src="https://github.com/user-attachments/assets/f2c6fdd1-a355-4639-9270-e1a597962e78" />

---

# 🔟 NTILE()

Divides records into equal-sized groups.

### Example

```sql
SELECT
employee_name,
salary,
NTILE(4)
OVER(ORDER BY salary DESC) AS quartile
FROM Employees;
```
# EXAMPLE: 

<img width="344" height="283" alt="image" src="https://github.com/user-attachments/assets/5ed9ef8a-74e9-4352-acb1-0236f980bcfb" />

### Use Cases

- Customer Segmentation
- Sales Analysis
- Top 25% Customers
- Quartile Analysis

---

# 1️⃣1️⃣ CUME_DIST()

Calculates cumulative distribution.

### Example

```sql
SELECT
salary,
CUME_DIST()
OVER(ORDER BY salary) AS cumulative_distribution
FROM Employees;
```

### Output

| Salary | CUME_DIST |
|---------|------------|
| 30000 | 0.25 |
| 40000 | 0.50 |
| 50000 | 0.75 |
| 60000 | 1.00 |
# EXAMPLE:

<img width="254" height="128" alt="image" src="https://github.com/user-attachments/assets/fdddcaa8-c611-4856-9f7b-3a9784d2d6c5" />

---

# 1️⃣2️⃣ LEAD()

Retrieves values from the next row.

### Example

```sql
SELECT
month,
sales,
LEAD(sales)
OVER(ORDER BY month) AS next_month_sales
FROM Sales;
```

### Use Cases

- Forecasting
- Trend Analysis
- Future Comparisons

---

# 1️⃣3️⃣ LAG()

Retrieves values from the previous row.

### Example

```sql
SELECT
month,
sales,
LAG(sales)
OVER(ORDER BY month) AS previous_month_sales
FROM Sales;
```

### Use Cases

- Growth Analysis
- Historical Comparisons
- Revenue Tracking
## EXAMPLES:
<img width="572" height="148" alt="image" src="https://github.com/user-attachments/assets/0adcb67a-82cc-4421-a5e1-bf975d632ae0" />

<img width="591" height="153" alt="image" src="https://github.com/user-attachments/assets/867446d3-a4c3-4a1f-9a86-0a393102a167" />

---

# 1️⃣4️⃣ FIRST_VALUE()

Returns the first value within a window.

### Example

```sql
SELECT
employee_name,
salary,
FIRST_VALUE(salary)
OVER(ORDER BY salary DESC)
AS highest_salary
FROM Employees;
```

---

# 1️⃣5️⃣ LAST_VALUE()

Returns the last value within a window.

### Example

```sql
SELECT
employee_name,
salary,
LAST_VALUE(salary)
OVER(
ORDER BY salary
ROWS BETWEEN UNBOUNDED PRECEDING
AND UNBOUNDED FOLLOWING
) AS lowest_salary
FROM Employees;
```
# COMBINED EXAMPLE:

<img width="516" height="190" alt="image" src="https://github.com/user-attachments/assets/ab4bddc5-9e39-4305-84e4-60aace6b4ba0" />

---

# 1️⃣6️⃣ Running Totals

Running totals are frequently used in business reporting.

### Example

```sql
SELECT
order_date,
sales_amount,
SUM(sales_amount)
OVER(ORDER BY order_date)
AS running_total
FROM Sales;
```

---

# 1️⃣7️⃣ Moving Averages

Moving averages help identify trends.
### THE WINDOW FRAME:

<img width="475" height="292" alt="image" src="https://github.com/user-attachments/assets/ec3c2110-df00-473d-899c-d844711cc698" />

<img width="730" height="230" alt="image" src="https://github.com/user-attachments/assets/2d093fa6-550e-4c52-bffc-57c97aa58310" />

### Example

```sql
SELECT
order_date,
sales_amount,
AVG(sales_amount)
OVER(
ORDER BY order_date
ROWS BETWEEN 2 PRECEDING AND CURRENT ROW
)
AS moving_average
FROM Sales;
```

---

# 1️⃣8️⃣ Real-World Business Use Cases

## Banking

Rank customers by account balance.

## E-Commerce

Identify top-selling products.

## HR Analytics

Rank employees by performance and salary.

## Sales Analytics

Track revenue growth using running totals.

## Stock Market

Calculate moving averages and trends.

## Education

Rank students based on marks.

---

# 1️⃣9️⃣ Common Mistakes

### ❌ Confusing RANK() and DENSE_RANK()

### ❌ Forgetting PARTITION BY

### ❌ Using GROUP BY Instead of Window Functions

### ❌ Missing ORDER BY in Ranking Functions

### ❌ Incorrect LAST_VALUE() Window Frame

---

# 📝 Practice Exercises

### Exercise 1

Assign row numbers to all employees.

### Exercise 2

Rank employees based on salary.

### Exercise 3

Use DENSE_RANK() on employee salaries.

### Exercise 4

Divide customers into four groups using NTILE().

### Exercise 5

Calculate cumulative salary distribution.

### Exercise 6

Find next month's sales using LEAD().

### Exercise 7

Find previous month's sales using LAG().

### Exercise 8

Display highest salary using FIRST_VALUE().

### Exercise 9

Display lowest salary using LAST_VALUE().

### Exercise 10

Calculate running sales totals.

### Exercise 11

Calculate a 3-month moving average.

### Exercise 12

Find the top 3 employees in each department.

### Exercise 13

Rank products by total sales.

### Exercise 14

Identify the top 10% customers.

### Exercise 15

Build a sales trend report using:
- LEAD()
- LAG()
- Running Totals

---

# 🎯 Key Takeaways

✅ Window Functions preserve row-level data.

✅ OVER() defines the calculation window.

✅ PARTITION BY creates logical groups.

✅ ROW_NUMBER() assigns unique row numbers.

✅ RANK() skips numbers after ties.

✅ DENSE_RANK() does not skip numbers.

✅ NTILE() divides data into equal groups.

✅ CUME_DIST() calculates cumulative distribution.

✅ LEAD() accesses future rows.

✅ LAG() accesses previous rows.

✅ Running Totals and Moving Averages are widely used in business dashboards.

---

# 📖 Day 17 Summary

Today, you learned Window Functions, one of the most important SQL concepts for analytics and reporting. These functions allow ranking, comparisons, trend analysis, cumulative calculations, and advanced reporting while preserving row-level detail.

Window Functions are heavily used in:

- Data Analytics
- Business Intelligence
- Financial Reporting
- HR Analytics
- E-Commerce Reporting
- SQL Interviews

---

## 🚀 Coming Up Next: Day 18 – Common Table Expressions (CTEs)

Topics Covered:

- WITH Clause
- Single CTE
- Multiple CTEs
- Recursive CTEs
- Hierarchical Queries
- Organizational Structures
- Tree Traversal

## Progress Status: Day 17 Completed ✅
---

[PREVIOUS: DAY16](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/01b9b9e353d86c5e2cb7e23b33ee2c59e8ba48b9/DAY16/DAY16%20-%20SQL%20Mastery%20Assessment%202.md)👆\
[NEXT: DAY18](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/4750d399ee75895a614668c2c63ec7cc87024474/DAY18/DAY18-%20Common%20Table%20Expressions%20(CTEs)%20%26%20Recursive%20CTEs.md)👇
