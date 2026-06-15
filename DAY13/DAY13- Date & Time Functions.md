# 🚀 30 Days of SQL – Day 13: Date & Time Functions

Welcome to **Day 13** of the **30 Days of SQL Challenge**!

In previous days, we learned how to create databases, retrieve data, filter records, group data, and combine results using Joins and Set Operations. Today, we will explore **Date & Time Functions**, one of the most commonly used topics in real-world SQL development.

Dates and timestamps are present in almost every database system, making these functions essential for reporting, analytics, auditing, and business intelligence.

---

# 📚 Table of Contents

1. Introduction to Date & Time Functions
2. Why Are Date Functions Important?
3. Understanding Date Datatypes
4. Current Date & Time Functions
5. Extracting Date Components
6. Date Arithmetic
7. Calculating Differences Between Dates
8. Formatting Dates
9. Working with Timestamps
10. Real-World Applications
11. Common Mistakes
12. Practice Exercises
13. Key Takeaways
14. Day 13 Summary

---

# 1️⃣ Introduction to Date & Time Functions

Date and Time Functions allow SQL to:

- Store dates
- Store timestamps
- Calculate durations
- Track events
- Generate reports
- Analyze trends
- Monitor system activity

Example:

```sql
SELECT CURRENT_DATE;
```

Output:

```text
2025-06-15
```

---

# 2️⃣ Why Are Date Functions Important?

Almost every business application stores date-related information.

## Banking

- Transaction dates
- Loan start dates
- Loan maturity dates

## E-Commerce

- Order dates
- Delivery dates
- Return dates

## Healthcare

- Appointment schedules
- Patient admission dates

## Human Resources

- Employee joining dates
- Attendance records
- Leave management

## Education

- Enrollment dates
- Examination schedules

---

# 3️⃣ Understanding Date Datatypes

SQL provides multiple datatypes for handling dates and times.

| Datatype | Description |
|-----------|-------------|
| DATE | Stores only date |
| TIME | Stores only time |
| DATETIME | Stores date and time |
| TIMESTAMP | Stores date and time with automatic tracking |
| YEAR | Stores year values |

### Example

```sql
CREATE TABLE Employees (
    employee_id INT,
    employee_name VARCHAR(100),
    joining_date DATE
);
```

---

# 4️⃣ Current Date & Time Functions

## CURRENT_DATE

Returns the current system date.

```sql
SELECT CURRENT_DATE;
```

Output:

```text
2025-06-15
```

---

## CURRENT_TIME

Returns the current system time.

```sql
SELECT CURRENT_TIME;
```

Example Output:

```text
14:30:45
```

---

## CURRENT_TIMESTAMP

Returns both current date and time.

```sql
SELECT CURRENT_TIMESTAMP;
```

Example Output:

```text
2025-06-15 14:30:45
```

---

## NOW()

Commonly used in MySQL.

```sql
SELECT NOW();
```

Output:

```text
2025-06-15 14:30:45
```

---

# 5️⃣ Extracting Date Components

Often we need to extract specific parts of a date.

Given:

```text
2025-06-15
```

---

## YEAR()

```sql
SELECT YEAR('2025-06-15');
```

Output:

```text
2025
```

---

## MONTH()

```sql
SELECT MONTH('2025-06-15');
```

Output:

```text
6
```

---

## DAY()

```sql
SELECT DAY('2025-06-15');
```

Output:

```text
15
```

---

## WEEKDAY()

Returns the weekday number.

```sql
SELECT WEEKDAY('2025-06-15');
```

---

# 6️⃣ Date Arithmetic

Date arithmetic allows adding or subtracting intervals from dates.

---

## DATE_ADD()

Add days, months, or years.

```sql
SELECT DATE_ADD('2025-06-15', INTERVAL 10 DAY);
```

Output:

```text
2025-06-25
```

---

## DATE_SUB()

Subtract intervals from dates.

```sql
SELECT DATE_SUB('2025-06-15', INTERVAL 5 DAY);
```

Output:

```text
2025-06-10
```

---

## Supported Intervals

```sql
DAY
MONTH
YEAR
HOUR
MINUTE
SECOND
```

---

# 7️⃣ Calculating Differences Between Dates

## DATEDIFF()

Returns the difference in days between two dates.

```sql
SELECT DATEDIFF(
    '2025-06-15',
    '2025-06-01'
);
```

Output:

```text
14
```

---

## TIMESTAMPDIFF()

Calculates differences in:

- Years
- Months
- Days
- Hours
- Minutes
- Seconds

Example:

```sql
SELECT TIMESTAMPDIFF(
    YEAR,
    '2000-01-01',
    CURRENT_DATE
);
```

---

# 8️⃣ Formatting Dates

Different regions use different date formats.

### Standard SQL Format

```text
2025-06-15
```

### Indian Format

```text
15-06-2025
```

---

## DATE_FORMAT()

```sql
SELECT DATE_FORMAT(
    '2025-06-15',
    '%d-%m-%Y'
);
```

Output:

```text
15-06-2025
```

---

## Common Format Specifiers

| Specifier | Meaning |
|------------|----------|
| %d | Day |
| %m | Month |
| %Y | Four-digit Year |
| %y | Two-digit Year |
| %H | Hour |
| %i | Minute |
| %S | Second |

---

# 9️⃣ Working with Timestamps

Timestamps are commonly used for audit tracking.

---

## Creating a Timestamp Column

```sql
CREATE TABLE Orders (
    order_id INT,
    order_date TIMESTAMP
);
```

---

## Automatic Timestamp Tracking

```sql
CREATE TABLE Orders (
    order_id INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

Every new record automatically stores its creation time.

---

# 🔟 Real-World Applications

## E-Commerce

Find orders placed today.

```sql
SELECT *
FROM Orders
WHERE order_date = CURRENT_DATE;
```

---

## Human Resources

Find employees who joined this year.

```sql
SELECT *
FROM Employees
WHERE YEAR(joining_date) = YEAR(CURRENT_DATE);
```

---

## Banking

Calculate loan duration.

```sql
SELECT DATEDIFF(maturity_date, start_date)
FROM Loans;
```

---

## Healthcare

Find upcoming appointments.

```sql
SELECT *
FROM Appointments
WHERE appointment_date > CURRENT_DATE;
```

---

## Business Analytics

Generate monthly sales reports.

```sql
SELECT MONTH(order_date),
       SUM(amount)
FROM Orders
GROUP BY MONTH(order_date);
```

---

# 1️⃣1️⃣ Common Mistakes

## Comparing Dates as Strings

❌ Incorrect

```sql
WHERE order_date = '15/06/2025'
```

---

## Ignoring Timestamp Values

❌ Incorrect

```sql
WHERE created_at = CURRENT_DATE
```

A timestamp contains both date and time.

---

## Using Wrong Date Formats

❌ Incorrect

```text
MM-DD-YYYY
```

When the database expects:

```text
YYYY-MM-DD
```

---

# 📝 Practice Exercises

## Exercise 1

Create an Employees table with:

- employee_id
- employee_name
- joining_date

Insert at least 5 records.

---

## Exercise 2

Display today's date using:

```sql
CURRENT_DATE
```

---

## Exercise 3

Display the current timestamp.

---

## Exercise 4

Extract:

- Year
- Month
- Day

from employee joining dates.

---

## Exercise 5

Find employees who joined after:

```text
2024-01-01
```

---

## Exercise 6

Add 30 days to the current date.

---

## Exercise 7

Calculate the difference between joining date and current date.

---

## Exercise 8

Format employee joining dates as:

```text
DD-MM-YYYY
```

---

## Exercise 9

Create an Orders table with automatic timestamp tracking.

---

## Exercise 10

Generate a report showing:

- Employee Name
- Joining Date
- Years of Service

---

# 🎯 Key Takeaways

✅ Dates are essential in almost every database system.

✅ CURRENT_DATE returns the current date.

✅ CURRENT_TIME returns the current time.

✅ CURRENT_TIMESTAMP returns both date and time.

✅ YEAR(), MONTH(), and DAY() extract date components.

✅ DATE_ADD() and DATE_SUB() perform date arithmetic.

✅ DATEDIFF() calculates differences between dates.

✅ DATE_FORMAT() changes how dates are displayed.

✅ TIMESTAMP helps track record creation and modification.

---

# 📖 Day 13 Summary

Today, you learned how SQL handles dates and time values. You explored date datatypes, current date functions, date arithmetic, date formatting, timestamp tracking, and date-based reporting techniques.

These functions are heavily used in business reporting, dashboards, auditing systems, analytics, and enterprise applications. Mastering date and time functions is a crucial step toward becoming proficient in SQL.

---

## 🚀 Coming Up Next: Day 14 – Exploratory Data Analysis (EDA) Using SQL

You'll learn:

```sql
COUNT()
DISTINCT
Duplicate Detection
Missing Values
Data Profiling
Frequency Analysis
Outlier Detection
Business Insights
```

and discover how analysts use SQL to explore, clean, and understand datasets before building reports and dashboards.

## Progress Status: Day 13 Completed ✅
---

[PREVIOUS: DAY12](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/ed47416e731effb3dd955c52e9bafeebd7dfdf93/DAY12/DAY12-%20SQL%20Set%20Operations.md) 👆
\
[NEXT: DAY14]() 👇


---
