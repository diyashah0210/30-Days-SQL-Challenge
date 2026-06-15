# 🚀 30 Days of SQL – Day 14: Exploratory Data Analysis (EDA) Using SQL

Welcome to **Day 14** of the **30 Days of SQL Challenge**!

So far, you've learned how to create databases, manipulate data, perform joins, use set operations, and work with date functions. Today, we'll explore one of the most important skills used by Data Analysts, Business Analysts, and Data Scientists before building reports or dashboards:

# 🔍 Exploratory Data Analysis (EDA)

EDA is the process of examining, understanding, cleaning, validating, and summarizing data before drawing conclusions from it.

---

# 📚 Table of Contents

1. What is Exploratory Data Analysis (EDA)?
2. Why is EDA Important?
3. The EDA Workflow
4. Understanding Dataset Structure
5. Counting Records
6. Finding Unique Values
7. Detecting Missing Values
8. Detecting Duplicate Records
9. Frequency Analysis
10. Basic Statistical Analysis
11. Finding Minimum & Maximum Values
12. Identifying Outliers
13. Data Distribution Analysis
14. Business Insight Generation
15. SQL Calculator Functions
16. Time Machine Functions – EXTRACT()
17. SQL Logic Builder – IF() & CASE
18. Real-World EDA Examples
19. Common Mistakes During EDA
20. Practice Exercises
21. Key Takeaways
22. Day 14 Summary

---

# 1️⃣ What is Exploratory Data Analysis (EDA)?

Exploratory Data Analysis (EDA) is the process of analyzing datasets to understand:

- Data Quality
- Data Completeness
- Patterns
- Trends
- Relationships
- Anomalies
- Business Insights

EDA helps answer questions like:

- Is the data clean?
- Are there missing values?
- Are there duplicate records?
- What trends exist?
- Are there unusual values?
- What business insights can be generated?

---

# 2️⃣ Why is EDA Important?

Imagine building a sales dashboard without checking the data first.

Potential issues:

❌ Duplicate Orders

❌ Missing Customer Names

❌ Invalid Dates

❌ Incorrect Sales Values

❌ Blank Product Categories

EDA helps identify these problems before they impact reports and decision-making.

---

# 3️⃣ The EDA Workflow

A typical SQL EDA workflow follows:

```text
Understand Dataset
        ↓
Count Records
        ↓
Check Missing Values
        ↓
Check Duplicates
        ↓
Analyze Categories
        ↓
Calculate Statistics
        ↓
Identify Outliers
        ↓
Generate Insights
```

---

# 4️⃣ Understanding Dataset Structure

Before analyzing data, understand:

- Number of Columns
- Datatypes
- Primary Keys
- Relationships
- Constraints

### Example

```sql
DESCRIBE Employees;
```

or

```sql
SHOW COLUMNS FROM Employees;
```

### Output

| Field | Type |
|---------|---------|
| employee_id | INT |
| employee_name | VARCHAR |
| salary | DECIMAL |
| joining_date | DATE |

---

# 5️⃣ Counting Records

The first step is usually determining dataset size.

## COUNT(*)

```sql
SELECT COUNT(*)
FROM Employees;
```

### Output

```text
250 Records
```

---

# 6️⃣ Finding Unique Values

Unique values help identify categories and dimensions.

## DISTINCT

```sql
SELECT DISTINCT department
FROM Employees;
```

### Output

```text
HR
IT
Finance
Marketing
```

---

## Count Unique Values

```sql
SELECT COUNT(DISTINCT department)
FROM Employees;
```

---

# 7️⃣ Detecting Missing Values

Missing values often lead to inaccurate analysis.

### Find Employees Without Emails

```sql
SELECT *
FROM Employees
WHERE email IS NULL;
```

---

### Count Missing Values

```sql
SELECT COUNT(*)
FROM Employees
WHERE email IS NULL;
```

---

# 8️⃣ Detecting Duplicate Records

Duplicate records can distort business metrics.

### Find Duplicate Employees

```sql
SELECT employee_name,
       COUNT(*)
FROM Employees
GROUP BY employee_name
HAVING COUNT(*) > 1;
```

---

### Find Duplicate Emails

```sql
SELECT email,
       COUNT(*)
FROM Employees
GROUP BY email
HAVING COUNT(*) > 1;
```

---

# 9️⃣ Frequency Analysis

Frequency analysis helps understand data distribution.

### Employees by Department

```sql
SELECT department,
       COUNT(*) AS total_employees
FROM Employees
GROUP BY department;
```

### Output

| Department | Employees |
|------------|------------|
| HR | 25 |
| IT | 80 |
| Finance | 40 |
| Marketing | 35 |

---

# 🔟 Basic Statistical Analysis

## Average Salary

```sql
SELECT AVG(salary)
FROM Employees;
```

---

## Total Salary Expense

```sql
SELECT SUM(salary)
FROM Employees;
```

---

## Highest Salary

```sql
SELECT MAX(salary)
FROM Employees;
```

---

## Lowest Salary

```sql
SELECT MIN(salary)
FROM Employees;
```

---

# 1️⃣1️⃣ Finding Minimum & Maximum Values

## Highest Paid Employee

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

## Lowest Paid Employee

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

# 1️⃣2️⃣ Identifying Outliers

Outliers are unusually high or low values.

### Example Dataset

| Employee | Salary |
|------------|---------|
| A | 50,000 |
| B | 52,000 |
| C | 55,000 |
| D | 60,000 |
| E | 500,000 |

Employee E is a potential outlier.

---

### Find High Salary Outliers

```sql
SELECT *
FROM Employees
WHERE salary > 200000;
```

---

# 1️⃣3️⃣ Data Distribution Analysis

Understanding how data is distributed helps identify trends.

### Salary Band Analysis

```sql
SELECT
CASE
    WHEN salary < 50000 THEN 'Low'
    WHEN salary BETWEEN 50000 AND 100000 THEN 'Medium'
    ELSE 'High'
END AS salary_band,
COUNT(*) AS total_employees
FROM Employees
GROUP BY salary_band;
```

---

# 1️⃣4️⃣ Business Insight Generation

EDA is ultimately about generating meaningful business insights.

## Department with Highest Employees

```sql
SELECT department,
       COUNT(*) AS total
FROM Employees
GROUP BY department
ORDER BY total DESC;
```

---

## City Generating Highest Revenue

```sql
SELECT city,
       SUM(sales_amount)
FROM Sales
GROUP BY city
ORDER BY SUM(sales_amount) DESC;
```

---

## Most Sold Product

```sql
SELECT product_name,
       COUNT(*)
FROM Orders
GROUP BY product_name
ORDER BY COUNT(*) DESC;
```

---

# 1️⃣5️⃣ SQL Calculator Functions

SQL provides built-in mathematical functions useful during analysis.

---

## ROUND()

Rounds a value to specified decimal places.

```sql
SELECT ROUND(123.4567, 2);
```

Output:

```text
123.46
```

---

## FLOOR()

Rounds down.

```sql
SELECT FLOOR(123.99);
```

Output:

```text
123
```

---

## CEILING()

Rounds up.

```sql
SELECT CEILING(123.01);
```

Output:

```text
124
```

---

## SQUARE()

Returns square of a number.

```sql
SELECT SQUARE(12);
```

Output:

```text
144
```

---

## SQRT()

Returns square root.

```sql
SELECT SQRT(144);
```

Output:

```text
12
```

---

## POWER()

Raises a number to a power.

```sql
SELECT POWER(2,5);
```

Output:

```text
32
```

---

## Business Example

```sql
SELECT
employee_name,
monthly_salary,
monthly_salary * 12 AS annual_salary
FROM Employees;
```

---

# 1️⃣6️⃣ Time Machine Functions – EXTRACT()

The EXTRACT() function retrieves specific parts from dates and timestamps.

---

## Syntax

```sql
SELECT EXTRACT(part FROM date_value);
```

---

## Extract Year

```sql
SELECT EXTRACT(YEAR FROM '2025-06-15');
```

Output:

```text
2025
```

---

## Extract Month

```sql
SELECT EXTRACT(MONTH FROM '2025-06-15');
```

Output:

```text
6
```

---

## Extract Day

```sql
SELECT EXTRACT(DAY FROM '2025-06-15');
```

Output:

```text
15
```

---

## Extract Hour

```sql
SELECT EXTRACT(HOUR FROM CURRENT_TIMESTAMP);
```

---

## Business Example

```sql
SELECT
EXTRACT(MONTH FROM order_date) AS month,
SUM(sales_amount)
FROM Orders
GROUP BY month;
```

---

# 1️⃣7️⃣ SQL Logic Builder – IF() & CASE

Business analysis often requires categorizing data.

---

## IF()

(MySQL)

```sql
SELECT
employee_name,
IF(salary > 100000,
   'High Salary',
   'Normal Salary')
AS category
FROM Employees;
```

---

## CASE Statement

The CASE statement allows multiple conditions.

```sql
SELECT
employee_name,
salary,
CASE
    WHEN salary > 100000 THEN 'High'
    WHEN salary >= 50000 THEN 'Medium'
    ELSE 'Low'
END AS salary_band
FROM Employees;
```

---

### Output

| Employee | Salary | Band |
|-----------|---------|---------|
| John | 120000 | High |
| Mary | 70000 | Medium |
| Alex | 30000 | Low |

---

## Age Categorization Example

```sql
SELECT
employee_name,
CASE
    WHEN age < 18 THEN 'Minor'
    WHEN age BETWEEN 18 AND 60 THEN 'Adult'
    ELSE 'Senior Citizen'
END AS age_group
FROM Employees;
```

---

# 1️⃣8️⃣ Real-World EDA Examples

## E-Commerce

- Most Sold Products
- Revenue by Category
- Customer Purchase Frequency

---

## Banking

- High Value Customers
- Loan Distribution
- Transaction Patterns

---

## Healthcare

- Patient Visits per Month
- Common Diseases
- Appointment Trends

---

## Education

- Student Performance Analysis
- Attendance Trends
- Course Popularity

---

## Human Resources

- Salary Distribution
- Employee Growth
- Retention Analysis

---

# 1️⃣9️⃣ Common Mistakes During EDA

## Ignoring Missing Values

❌ Leads to inaccurate reports.

---

## Ignoring Duplicate Records

❌ Inflates business metrics.

---

## Looking Only at Averages

❌ Can hide outliers.

---

## Skipping Data Validation

❌ Garbage In = Garbage Out.

---

# 📝 Practice Exercises

## Exercise 1

Create an Employees table with:

- employee_id
- employee_name
- department
- salary
- email

Insert at least 10 records.

---

## Exercise 2

Count total employees.

---

## Exercise 3

Find unique departments.

---

## Exercise 4

Count employees in each department.

---

## Exercise 5

Find employees with missing email addresses.

---

## Exercise 6

Find duplicate employee names.

---

## Exercise 7

Calculate:

- Average Salary
- Maximum Salary
- Minimum Salary
- Total Salary Expense

---

## Exercise 8

Identify employees earning more than ₹200,000.

---

## Exercise 9

Create salary bands:

- Low
- Medium
- High

---

## Exercise 10

Generate three business insights from the employee dataset.

---

## Exercise 11

Use ROUND() to round salary values.

---

## Exercise 12

Use FLOOR() and CEILING() on salary values.

---

## Exercise 13

Use SQUARE(), SQRT(), and POWER() functions.

---

## Exercise 14

Extract Year, Month, and Day from joining dates.

---

## Exercise 15

Create salary categories using IF().

---

## Exercise 16

Create employee grading using CASE statements.

---

## Exercise 17

Create age groups using CASE.

---

# 🎯 Key Takeaways

✅ EDA is the foundation of data analysis.

✅ COUNT() measures dataset size.

✅ DISTINCT identifies unique values.

✅ NULL checks help find missing data.

✅ GROUP BY enables frequency analysis.

✅ Aggregate functions summarize data.

✅ ROUND(), FLOOR(), CEILING(), SQRT(), and POWER() support calculations.

✅ EXTRACT() retrieves date components.

✅ IF() and CASE help categorize data.

✅ EDA transforms raw data into meaningful insights.

---

# 📖 Day 14 Summary

Today, you learned how to perform Exploratory Data Analysis (EDA) using SQL. You explored methods for understanding datasets, validating data quality, detecting missing and duplicate records, analyzing distributions, performing calculations, extracting date components, applying business logic, and generating insights.

EDA is one of the most valuable skills for Data Analysts, Business Analysts, Data Scientists, and SQL Developers because every successful data project begins with understanding the data.

|SR. NO. | FUNCTION  | WHAT IT DOES? | EXAMPLE/SYNTAX | OUTPUT |
| ------- | -------- | ------------  | -------------- | ------ |
|1.| ROUND(x,d)| Rounds to 'd' decimal places | ``` ROUND(3.14125,2)```| ``` 3.14 ```|
|2.|FLOOR(x)| Rounds down to nearest whole number | ```  FLOOR(3.9)```| ``` 3 ```|
|3.| CEILING(x)| Rounds up to nearest whole number | ``` CEILING(3.9)```| ``` 4 ```|
|4.| SQUARE(x)| Results in square of x | ``` SQUARE(3)```| ``` 9 ```|
|5.| SQRT(x)| Results in square root of x | ``` SQRT(16)```| ``` 4 ```|
|6.| POWER(x,y)| Raises 'x' to the power 'y' | ``` POWER(2,3)```| ``` 8 ```|
|7.| EXTRACT()| To extract specific parts of the date | ``` EXTRACT(YEAR from date)```| ``` 12 ```|
|8.| IF()| Conditioning | ``` IF(gpa>3.5,"GOOD","BAD")```| ``` input:3---> BAD```|
|   |      |             |                              | ``` input:4---> GOOD```|
|9. | WHEN CASE| COnditioning| ``` CASE WHEN gpa>3.5 THEN "GOOD" , WHEN gpa< 3.5 THEN "BAD" ELSE "WORST" END ```|``` input:3---> BAD```|
|   |      |             |                              | ``` input:4---> GOOD```|

---

## 🚀 Coming Up Next: Day 15 – Advanced Aggregate Functions & KPI Analysis

You'll learn:

```sql
COUNT(DISTINCT)
Conditional Aggregation
Nested Aggregation
Running Totals
Business KPIs
Revenue Analysis
Profit Analysis
Department-wise Analytics
```

and discover how organizations use SQL to calculate key performance indicators and make data-driven decisions.

## Progress Status: Day 14 Completed ✅
---
[PREVIOUS: DAY13](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/e322e6dcb403a8e42f9ec6fb892f31bb44d506be/DAY13/DAY13-%20Date%20%26%20Time%20Functions.md)👆\
[NEXT: DAY15](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/153550015db8bf07c8df07b4362082491c76f392/DAY15/DAY15-%20Advanced%20Aggregate%20Functions%20%26%20KPI%20Analysis.md)👇
