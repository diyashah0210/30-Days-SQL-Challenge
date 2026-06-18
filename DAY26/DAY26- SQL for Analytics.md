# 📘 30 Days Of SQL: Day 26 - SQL for Analytics

Welcome to **Day 26** of the **30 Days of SQL** challenge! 🎉

So far, we've learned how to design databases, write queries, create views, optimize performance, automate tasks, and manage data.

Today, we'll explore how SQL is used for **Analytics**, one of the most powerful and in-demand applications of SQL.

SQL Analytics helps businesses answer questions such as:

- Which products generate the most revenue?
- Who are our top customers?
- Which department performs best?
- What are the monthly sales trends?
- Which region contributes the highest profit?

---

# 📚 Table of Contents

1. Overview
2. What is SQL Analytics?
3. Why Analytics is Important
4. Types of Business Analytics
5. KPI Analysis
6. Revenue Analysis
7. Profit Analysis
8. Customer Analytics
9. Sales Analytics
10. Product Analytics
11. Employee Analytics
12. Time-Based Analysis
13. Cohort Analysis Basics
14. Ranking Analysis
15. Trend Analysis
16. Comparative Analysis
17. Dashboard Queries
18. Real-World Case Studies
19. Common Mistakes
20. Hands-On Challenge
21. Practice Exercises
22. Key Takeaways
23. Day 26 Summary

---

# 🔍 Overview

Analytics is the process of converting raw data into meaningful insights.

SQL helps organizations:

✅ Identify trends

✅ Monitor business performance

✅ Track KPIs

✅ Predict future growth

✅ Support decision-making

---

# 📈 What is SQL Analytics?

SQL Analytics involves analyzing data using SQL queries to discover patterns, trends, and business insights.

Instead of simply retrieving data:

```sql
SELECT *
FROM Orders;
```

We analyze it:

```sql
SELECT
    MONTH(order_date),
    SUM(order_amount)
FROM Orders
GROUP BY MONTH(order_date);
```

This provides useful business information.

---

# 🎯 Why Analytics is Important

Without Analytics:

```text
Data → Stored
```

With Analytics:

```text
Data → Information → Insight → Business Decision
```

Benefits:

✅ Better Decision Making

✅ Improved Revenue

✅ Cost Reduction

✅ Increased Efficiency

✅ Business Growth

---

# 📊 Types of Business Analytics

## Descriptive Analytics

"What happened?"

Example:

```sql
SELECT SUM(sales_amount)
FROM Sales;
```

---

## Diagnostic Analytics

"Why did it happen?"

Example:

Compare sales by region.

---

## Predictive Analytics

"What might happen?"

Uses historical data to forecast trends.

---

## Prescriptive Analytics

"What should we do?"

Combines analytics and business strategy.

---

# 🎯 KPI Analysis

KPI = Key Performance Indicator

Common KPIs:

- Revenue
- Profit
- Sales
- Customer Retention
- Employee Productivity

Example:

```sql
SELECT
    SUM(order_amount) AS total_revenue
FROM Orders;
```

---

# 💰 Revenue Analysis

Calculate total revenue:

```sql
SELECT
    SUM(order_amount) AS revenue
FROM Orders;
```

Monthly Revenue:

```sql
SELECT
    YEAR(order_date),
    MONTH(order_date),
    SUM(order_amount) AS revenue
FROM Orders
GROUP BY
    YEAR(order_date),
    MONTH(order_date);
```

---

# 💵 Profit Analysis

Formula:

```text
Profit = Revenue - Cost
```

Example:

```sql
SELECT
    product_name,
    SUM(sales_amount - cost_amount) AS profit
FROM Sales
GROUP BY product_name;
```

---

# 👥 Customer Analytics

Top Customers:

```sql
SELECT
    customer_id,
    SUM(order_amount) AS total_spent
FROM Orders
GROUP BY customer_id
ORDER BY total_spent DESC;
```

Customer Count:

```sql
SELECT COUNT(*) AS customers
FROM Customers;
```

---

# 🛒 Sales Analytics

Total Sales:

```sql
SELECT SUM(order_amount)
FROM Orders;
```

Average Order Value:

```sql
SELECT AVG(order_amount)
FROM Orders;
```

Highest Sale:

```sql
SELECT MAX(order_amount)
FROM Orders;
```

---

# 📦 Product Analytics

Best Selling Products:

```sql
SELECT
    product_name,
    SUM(quantity)
FROM Order_Items
GROUP BY product_name
ORDER BY SUM(quantity) DESC;
```

Least Selling Products:

```sql
SELECT
    product_name,
    SUM(quantity)
FROM Order_Items
GROUP BY product_name
ORDER BY SUM(quantity);
```

---

# 👨‍💼 Employee Analytics

Department Performance:

```sql
SELECT
    department,
    AVG(salary)
FROM Employees
GROUP BY department;
```

Employee Count:

```sql
SELECT
    department,
    COUNT(*)
FROM Employees
GROUP BY department;
```

---

# 📅 Time-Based Analysis

Daily Sales:

```sql
SELECT
    order_date,
    SUM(order_amount)
FROM Orders
GROUP BY order_date;
```

Monthly Sales:

```sql
SELECT
    MONTH(order_date),
    SUM(order_amount)
FROM Orders
GROUP BY MONTH(order_date);
```

Yearly Sales:

```sql
SELECT
    YEAR(order_date),
    SUM(order_amount)
FROM Orders
GROUP BY YEAR(order_date);
```

---

# 👥 Cohort Analysis Basics

Cohort Analysis groups users based on shared characteristics.

Example:

Customers grouped by signup month.

```sql
SELECT
    MONTH(signup_date),
    COUNT(*)
FROM Customers
GROUP BY MONTH(signup_date);
```

Used for:

- Retention Analysis
- Customer Lifecycle Tracking
- Subscription Businesses

---

# 🏆 Ranking Analysis

Top 5 Customers:

```sql
SELECT
    customer_id,
    SUM(order_amount) AS spending
FROM Orders
GROUP BY customer_id
ORDER BY spending DESC
LIMIT 5;
```

---

# 📈 Trend Analysis

Identify growth patterns.

Example:

```sql
SELECT
    MONTH(order_date),
    SUM(order_amount)
FROM Orders
GROUP BY MONTH(order_date)
ORDER BY MONTH(order_date);
```

Used to visualize:

- Sales Trends
- Revenue Trends
- Customer Growth

---

# ⚖ Comparative Analysis

Compare regions.

```sql
SELECT
    region,
    SUM(sales_amount)
FROM Sales
GROUP BY region;
```

Compare departments.

```sql
SELECT
    department,
    AVG(salary)
FROM Employees
GROUP BY department;
```

---

# 📊 Dashboard Queries

Business dashboards typically display:

### Revenue

```sql
SELECT SUM(order_amount)
FROM Orders;
```

### Total Customers

```sql
SELECT COUNT(*)
FROM Customers;
```

### Total Orders

```sql
SELECT COUNT(*)
FROM Orders;
```

### Average Order Value

```sql
SELECT AVG(order_amount)
FROM Orders;
```

---

# 🏢 Real-World Case Studies

## E-Commerce

- Best Selling Products
- Customer Lifetime Value
- Monthly Revenue

---

## Banking

- Account Growth
- Loan Performance
- Customer Retention

---

## HR

- Employee Attrition
- Salary Analysis
- Department Performance

---

## Healthcare

- Patient Visits
- Treatment Trends
- Doctor Performance

---

# ❌ Common Mistakes

### ❌ Ignoring NULL Values

```sql
AVG(column_name)
```

May produce unexpected results.

---

### ❌ Wrong GROUP BY Usage

Always group non-aggregated columns.

---

### ❌ Using SELECT *

Select only required columns.

---

### ❌ Ignoring Date Analysis

Time trends are often the most valuable insights.

---

# 🎨 Hands-On Challenge

1. Find the top 10 customers by revenue.
2. Calculate monthly revenue.
3. Find the most profitable product.
4. Determine the best-performing department.
5. Create a mini business dashboard using SQL queries.

---

# 💻 Practice Exercises

## ✅ Level 1

1. Calculate total revenue.
2. Calculate average order value.
3. Find the highest sale.
4. Count total customers.
5. Find monthly sales.

## 🚀 Level 2

1. Identify top 5 customers.
2. Analyze department performance.
3. Calculate product profitability.
4. Create quarterly revenue reports.
5. Build a complete analytics dashboard query set.

---

# 🎯 Key Takeaways

✅ SQL is one of the most important analytics tools.

✅ Analytics transforms data into business insights.

✅ KPI analysis measures business performance.

✅ Revenue and profit analysis support decision-making.

✅ Customer and product analytics drive growth.

✅ Time-based analysis identifies trends.

✅ Dashboard queries summarize key metrics.

✅ Analytics is heavily used in Data Analyst, Business Analyst, and Data Science roles.

---

# 📝 Day 26 Summary

Today, you learned how SQL is used beyond data storage and retrieval to generate business insights. You explored KPI analysis, revenue tracking, profitability calculations, customer analytics, trend analysis, dashboard reporting, and real-world business use cases.

These skills are among the most valuable applications of SQL in modern organizations and form the foundation of data-driven decision making.

---

## 🚀 Coming Up Next: Day 27 – Error Handling & Exception Management

### Topics Covered

- SQL Errors
- TRY...CATCH
- Exception Handling
- Transaction Rollbacks
- Error Logging
- Debugging Queries
- Best Practices

## Progress Status: Day 26 Completed ✅
[PREVIOUS: DAY25-DATA IMPORT AND EXPORT](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/c89b78382d4335e196e8a8f92bf9b1edbf93d5b2/DAY25/DAY25-%20Data%20Import%20%26%20Export.md)👆\
[NEXT: DAY27-ERROR HANDLING & MANAGEMENT](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/c89b78382d4335e196e8a8f92bf9b1edbf93d5b2/DAY27/DAY27-%20Error%20Handling%20%26%20Exception%20Management.md)👇
