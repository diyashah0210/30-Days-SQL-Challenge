# 🚀 30 Days of SQL – Day 7: Sorting & Limiting Data

Welcome to **Day 7** of the **30 Days of SQL Challenge**!

In Day 6, you learned how to filter data using:

* WHERE
* AND
* OR
* NOT
* IN
* BETWEEN
* LIKE

Filtering helps us retrieve only the required records. However, once the data is retrieved, we often need to arrange it in a meaningful order.

Imagine viewing a list of 10,000 employees. Wouldn't it be easier if they were sorted by salary, age, or name?

This is where SQL sorting and limiting techniques become essential.

---

# 📚 Table of Contents

1. Why Sorting is Important
2. Understanding ORDER BY
3. Ascending Order (ASC)
4. Descending Order (DESC)
5. Sorting by Multiple Columns
6. Sorting with WHERE Clause
7. Limiting Results with LIMIT
8. Using TOP (SQL Server)
9. OFFSET Clause
10. FETCH Clause
11. Pagination in SQL
12. Combining Filtering and Sorting
13. Practice Exercises
14. Key Takeaways
15. Day 7 Summary

---

# 1️⃣ Why Sorting is Important

Imagine a library containing thousands of books.

A visitor asks:

> Show me the most recently published books.

Without sorting, the books would appear randomly.

Sorting helps us:

✅ Organize information

✅ Improve readability

✅ Generate professional reports

✅ Find highest and lowest values quickly

✅ Build dashboards and analytics

---

# 📖 Library Analogy

| Requirement                  | SQL Solution                   |
| ---------------------------- | ------------------------------ |
| Arrange books alphabetically | ORDER BY title                 |
| Show newest books first      | ORDER BY publication_year DESC |
| Show cheapest books first    | ORDER BY price ASC             |
| Display top 10 books         | LIMIT 10                       |

---

# 2️⃣ Understanding ORDER BY

The **ORDER BY** clause is used to sort query results.

## Syntax

```sql
SELECT column_name
FROM table_name
ORDER BY column_name;
```

By default, SQL sorts data in ascending order.

---

# Sample Students Table

| student_id | student_name | age |
| ---------- | ------------ | --- |
| 101        | Diya         | 23  |
| 102        | Aryaman      | 18  |
| 103        | Sam          | 25  |
| 104        | Riya         | 21  |

---

# 3️⃣ Ascending Order (ASC)

Ascending order means:

```text
Smallest → Largest
A → Z
Oldest → Newest
```

## Syntax

```sql
SELECT *
FROM Students
ORDER BY age ASC;
```

### Output

| student_name | age |
| ------------ | --- |
| Aryaman      | 18  |
| Riya         | 21  |
| Diya         | 23  |
| Sam          | 25  |

---

## Sorting Names Alphabetically

```sql
SELECT *
FROM Students
ORDER BY student_name ASC;
```

### Output

```text
Aryaman
Diya
Riya
Sam
```

---

# 4️⃣ Descending Order (DESC)

Descending order means:

```text
Largest → Smallest
Z → A
Newest → Oldest
```

## Syntax

```sql
SELECT *
FROM Students
ORDER BY age DESC;
```

### Output

| student_name | age |
| ------------ | --- |
| Sam          | 25  |
| Diya         | 23  |
| Riya         | 21  |
| Aryaman      | 18  |

---

## Example

```sql
SELECT *
FROM Employees
ORDER BY salary DESC;
```

Displays employees with highest salaries first.

---

# 5️⃣ Sorting by Multiple Columns

Sometimes one column isn't enough.

SQL allows sorting using multiple columns.

## Syntax

```sql
SELECT *
FROM table_name
ORDER BY column1, column2;
```

---

## Example

```sql
SELECT *
FROM Employees
ORDER BY department ASC, salary DESC;
```

### What Happens?

1. Employees are grouped by department.
2. Within each department, salaries are sorted from highest to lowest.

---

# Example Output

| department | salary |
| ---------- | ------ |
| HR         | 70000  |
| HR         | 50000  |
| IT         | 90000  |
| IT         | 80000  |

---

# 6️⃣ Sorting with WHERE Clause

Filtering and sorting are often used together.

## Syntax

```sql
SELECT *
FROM table_name
WHERE condition
ORDER BY column_name;
```

---

## Example

```sql
SELECT *
FROM Students
WHERE age > 18
ORDER BY age DESC;
```

### Process

Step 1: Filter students older than 18.

Step 2: Sort them from highest age to lowest age.

---

# 7️⃣ Limiting Results with LIMIT

Sometimes we only need a few records.

The **LIMIT** clause restricts the number of rows returned.

## Syntax

```sql
SELECT *
FROM table_name
LIMIT number;
```

---

## Example

```sql
SELECT *
FROM Students
LIMIT 3;
```

Displays only the first 3 records.

---

## Top Highest Salaries

```sql
SELECT *
FROM Employees
ORDER BY salary DESC
LIMIT 5;
```

Displays the top 5 highest-paid employees.

---

# 8️⃣ Using TOP (SQL Server)

SQL Server uses TOP instead of LIMIT.

## Syntax

```sql
SELECT TOP 5 *
FROM Employees;
```

---

## Example

```sql
SELECT TOP 10 *
FROM Students;
```

Returns the first 10 rows.

---

# LIMIT vs TOP

| MySQL | SQL Server |
| ----- | ---------- |
| LIMIT | TOP        |

---

# 9️⃣ OFFSET Clause

OFFSET skips a specified number of rows.

## Syntax

```sql
SELECT *
FROM table_name
LIMIT 5 OFFSET 10;
```

---

### Meaning

```text
Skip first 10 rows
Then display next 5 rows
```

---

## Example

```sql
SELECT *
FROM Students
LIMIT 10 OFFSET 20;
```

Returns rows 21–30.

---

# 🔟 FETCH Clause

FETCH is commonly used with OFFSET.

## Syntax

```sql
SELECT *
FROM Students
ORDER BY student_id
OFFSET 10 ROWS
FETCH NEXT 5 ROWS ONLY;
```

---

### Meaning

```text
Skip first 10 rows
Fetch next 5 rows
```

---

# 1️⃣1️⃣ Pagination in SQL

Pagination is heavily used in websites and applications.

Examples:

* Amazon product pages
* Flipkart search results
* LinkedIn job listings
* Instagram followers list

---

## Page Size = 10 Records

### Page 1

```sql
SELECT *
FROM Students
LIMIT 10 OFFSET 0;
```

---

### Page 2

```sql
SELECT *
FROM Students
LIMIT 10 OFFSET 10;
```

---

### Page 3

```sql
SELECT *
FROM Students
LIMIT 10 OFFSET 20;
```

---

# 1️⃣2️⃣ Combining Filtering and Sorting

Real-world queries often combine:

* WHERE
* ORDER BY
* LIMIT

---

## Example

```sql
SELECT *
FROM Employees
WHERE department = 'IT'
ORDER BY salary DESC
LIMIT 3;
```

### Output

Top 3 highest-paid employees from IT department.

---

# Query Execution Order

Even though we write:

```sql
SELECT
FROM
WHERE
ORDER BY
LIMIT
```

SQL processes:

```text
1. FROM
2. WHERE
3. SELECT
4. ORDER BY
5. LIMIT
```

Understanding this helps write efficient queries.

---

# 📝 Practice Exercises

### Exercise 1

Display all students sorted by age in ascending order.

---

### Exercise 2

Display all students sorted by age in descending order.

---

### Exercise 3

Display employees sorted by salary from highest to lowest.

---

### Exercise 4

Display students older than 18 and sort them by name.

---

### Exercise 5

Display the first 5 records from the Students table.

---

### Exercise 6

Display the top 3 highest-paid employees.

---

### Exercise 7

Display records 11–20 using LIMIT and OFFSET.

---

### Exercise 8

Sort employees by department and salary.

---

# 🎯 Key Takeaways

✅ Learned the purpose of sorting data

✅ Understood ORDER BY

✅ Learned ASC sorting

✅ Learned DESC sorting

✅ Sorted using multiple columns

✅ Combined WHERE and ORDER BY

✅ Limited results using LIMIT

✅ Learned TOP for SQL Server

✅ Used OFFSET and FETCH

✅ Understood Pagination

---

# 📖 Day 7 Summary

Today, you learned how to organize query results using ORDER BY and how to restrict the number of rows returned using LIMIT, TOP, OFFSET, and FETCH.

Sorting and limiting data are among the most commonly used SQL techniques because they improve readability, reporting, and application performance. These concepts are essential for real-world database applications, dashboards, and analytics systems.

---

## 🚀 Coming Up Next: Day 8 – SQL Functions

You'll learn:

```sql
COUNT()
SUM()
AVG()
MIN()
MAX()
ROUND()
UPPER()
LOWER()
LENGTH()
CONCAT()
```

and understand how SQL functions help perform calculations and manipulate data efficiently.

## Progress Status: Day 7 Completed ✅
---
[PREVIOUS: DAY6](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/0ac9ca2baf63e29a8dea8dcc4ba6d4f3810d738f/DAY6/DAY6-Filtering%20Data%20with%20WHERE%20Clause.md)👆\
[NEXT: DAY8](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/main/DAY8/DAY8-SQL%20Functions.md)👇
