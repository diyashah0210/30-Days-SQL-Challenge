# 🚀 30 Days of SQL – Day 10: SQL Assessment-1
Welcome to **Day 10** of the **30 Days of SQL Challenge**!

Congratulations on completing the first phase of your SQL learning journey. 🎉

Over the past nine days, you've learned:
# 🎯 Topics Covered

### Day 1

* Introduction to SQL
* Databases

### Day 2

* CREATE DATABASE
* CREATE TABLE
* INSERT
* Data Types
* Keys

### Day 3

* Relationships
* ER Diagrams
* Constraints

### Day 4

* DDL, DML, DQL, DCL, TCL

### Day 5

* SELECT
* INSERT
* UPDATE
* DELETE
* TRUNCATE

### Day 6

* WHERE
* AND
* OR
* NOT
* IN
* BETWEEN
* LIKE

### Day 7

* ORDER BY
* LIMIT
* OFFSET

### Day 8

* SQL Functions

### Day 9

* GROUP BY
* HAVING
* Subqueries


Today is a dedicated **Assessment Day** designed to evaluate your understanding before moving on to advanced SQL concepts such as Joins.

---

# 📚 Assessment Structure

| Section | Difficulty | MCQs | 
| ------- | ---------- | ---- | 
| MCQS    | Easy       | 5    | 
|         | Medium     | 5    | 
|         | Difficult  | 5    | 
| Practical | Easy       | 5    | 
|           | Medium     | 5    | 
|           | Difficult  | 5    |
| Total   | —          | 30   |

**Total Questions: 30**

---

## MCQ 1

What does SQL stand for?

A. Structured Query Language

B. Standard Query Logic

C. Structured Question Language

D. System Query Language

---

## MCQ 2

Which command creates a new database?

A. MAKE DATABASE

B. CREATE DATABASE

C. NEW DATABASE

D. ADD DATABASE

---

## MCQ 3

Which data type is best suited for storing names?

A. INT

B. DATE

C. VARCHAR

D. FLOAT

---

## MCQ 4

Which key uniquely identifies each record in a table?

A. Foreign Key

B. Candidate Key

C. Composite Key

D. Primary Key

---

## MCQ 5

Which SQL category contains the CREATE TABLE command?

A. DML

B. DQL

C. DDL

D. TCL

---


## MCQ 6

Which clause is used to filter records?

A. HAVING

B. GROUP BY

C. WHERE

D. ORDER BY

---

## MCQ 7

Which operator is used to check multiple values?

A. LIKE

B. IN

C. BETWEEN

D. NOT

---

## MCQ 8

What wildcard represents multiple characters in a LIKE condition?

A. _

B. %

C. *

D. #

---

## MCQ 9

What is the default sorting order in SQL?

A. DESC

B. ASC

C. RANDOM

D. NONE

---

## MCQ 10

Which function is used to count records?

A. AVG()

B. SUM()

C. COUNT()

D. MAX()

---

## MCQ 11

Which statement correctly describes WHERE and HAVING?

A. No difference exists between them

B. WHERE filters rows while HAVING filters groups

C. HAVING filters rows while WHERE filters groups

D. Both filter grouped data

---

## MCQ 12

What will the following query return?

```sql
SELECT department,
       COUNT(*)
FROM Employees
GROUP BY department;
```

A. Total number of employees

B. Employee count per department

C. Department names only

D. None of the above

---

## MCQ 13

What is a Subquery?

A. Backup table

B. Nested query

C. Temporary database

D. Relationship

---

## MCQ 14

Which clause is typically used before HAVING?

A. ORDER BY

B. WHERE

C. GROUP BY

D. LIMIT

---

## MCQ 15

What will this query return?

```sql
SELECT department,
       AVG(salary)
FROM Employees
GROUP BY department
HAVING AVG(salary) > 50000;
```

A. Departments with average salary greater than ₹50,000

B. Employees earning more than ₹50,000

C. Total salary of employees

D. All departments

---
## Practical 1

Create a database named:

```sql
CompanyDB
```

---

## Practical 2

Create an Employees table with the following columns:

```text
employee_id
employee_name
salary
department
```

---

## Practical 3

Insert three employee records into the Employees table.

---

## Practical 4

Display all records from the Employees table.

---

## Practical 5

Update the salary of an employee.

---
## Practical 6

Display employees earning more than ₹50,000.

---

## Practical 7

Display all employees belonging to the IT department.

---

## Practical 8

Display employees whose names start with the letter 'A'.

---

## Practical 9

Display employees sorted by salary in descending order.

---

## Practical 10

Find the following using SQL Functions:

* Total Employees
* Total Salary
* Average Salary

---

## Practical 11

Given the following Sales table:

| salesperson | region | sales_amount |
| ----------- | ------ | ------------ |
| Alice       | North  | 5000         |
| Bob         | South  | 7000         |
| Alice       | North  | 3000         |
| Bob         | South  | 2000         |
| Carol       | East   | 8000         |

Write a query to find the total sales for each region.

---

## Practical 12

Given the following Students table:

| class | student_name | score |
| ----- | ------------ | ----- |
| A     | John         | 85    |
| A     | Mary         | 90    |
| B     | Jake         | 70    |
| B     | Emily        | 75    |
| A     | Steve        | 95    |

Write a query to find the average score for each class.

---

## Practical 13

Using the Sales table above, write a query to find salespersons whose total sales exceed ₹8,000.

---

## Practical 14

Write a query to find students who appear more than once in a table.

---

## Practical 15

Write a query to find employees earning more than the average salary using a Subquery.

---

# ⭐ Bonus Challenge

Given the following Orders table:

| customer_id | order_amount |
| ----------- | ------------ |
| 1           | 100          |
| 2           | 200          |
| 1           | 300          |
| 2           | 400          |
| 3           | 500          |

Write a query to find customers whose total order amount exceeds ₹400.

---

# 🏆 Scoring Guide

| Score    | Level               |
| -------- | ------------------- |
| 27–30    | SQL Master 🌟       |
| 23–26    | SQL Advanced 🚀     |
| 18–22    | SQL Intermediate 📚 |
| 12–17    | SQL Beginner 🔰     |
| Below 12 | Needs Revision 📖   |

---

# 🎯 Key Takeaways

✅ Revised SQL Fundamentals

✅ Practiced Data Definition & Manipulation

✅ Reinforced Filtering & Sorting Concepts

✅ Applied SQL Functions

✅ Tested GROUP BY & HAVING

✅ Solved Real-World SQL Problems

✅ Prepared for Advanced SQL Topics

---

# 📖 Day 10 Summary

Day 10 served as a comprehensive assessment of everything covered from Day 1 through Day 9. The combination of conceptual questions and practical SQL challenges ensures that you've built a strong foundation before progressing to more advanced database concepts.

Take time to solve every question without referring to notes. The goal is not just to get the correct answer but to develop confidence in writing SQL queries independently.

---

## 🚀 Coming Up Next: Day 11 – SQL Joins

You'll learn:

```sql
INNER JOIN
LEFT JOIN
RIGHT JOIN
FULL OUTER JOIN
SELF JOIN
CROSS JOIN
```

and understand how relational databases combine data across multiple related tables.

**Progress Status:** Day 10 Completed ✅
---
[PREVIOUS: DAY9](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/03783536201c76b4aab88e2e43f4db3f052e0f1d/DAY9/DAY9-GROUP%20BY%2C%20HAVING%20%26%20Subqueries.md)👆\
[NEXT: DAY11](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/03783536201c76b4aab88e2e43f4db3f052e0f1d/DAY11/DAY11-%20SQL%20Joins%20Fundamentals.md)👇
