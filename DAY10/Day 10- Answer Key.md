# 🚀 30 Days of SQL – Day 10 Answer Key

## SQL Mastery Assessment Solutions

This document contains the complete solutions for all 30 questions from the Day 10 SQL Mastery Assessment.

---

## MCQ Answers

| Question | Answer |
| -------- | ------ |
| 1        | A      |
| 2        | B      |
| 3        | C      |
| 4        | D      |
| 5        | C      |
| 6        | C      |
| 7        | B      |
| 8        | B      |
| 9        | B      |
| 10       | C      |
| 11       | B      |
| 12       | B      |
| 13       | B      |
| 14       | C      |
| 15       | A      |

---

## Practical 1

### Create Database

```sql
CREATE DATABASE CompanyDB;
```

---

## Practical 2

### Create Employees Table

```sql
CREATE TABLE Employees (
    employee_id INT PRIMARY KEY,
    employee_name VARCHAR(100) NOT NULL,
    salary DECIMAL(10,2),
    department VARCHAR(50)
);
```

---

## Practical 3

### Insert Records

```sql
INSERT INTO Employees
VALUES
(1, 'John', 50000, 'HR'),
(2, 'Sarah', 70000, 'IT'),
(3, 'Mike', 60000, 'Finance');
```

---

## Practical 4

### Display All Employees

```sql
SELECT *
FROM Employees;
```

---

## Practical 5

### Update Salary

```sql
UPDATE Employees
SET salary = 75000
WHERE employee_id = 2;
```

---
## Practical 6

### Employees Earning More Than ₹50,000

```sql
SELECT *
FROM Employees
WHERE salary > 50000;
```

---

## Practical 7

### Employees in IT Department

```sql
SELECT *
FROM Employees
WHERE department = 'IT';
```

---

## Practical 8

### Names Starting with 'A'

```sql
SELECT *
FROM Employees
WHERE employee_name LIKE 'A%';
```

---

## Practical 9

### Sort Employees by Salary Descending

```sql
SELECT *
FROM Employees
ORDER BY salary DESC;
```

---

## Practical 10

### Total Employees

```sql
SELECT COUNT(*)
FROM Employees;
```

### Total Salary

```sql
SELECT SUM(salary)
FROM Employees;
```

### Average Salary

```sql
SELECT AVG(salary)
FROM Employees;
```

---

## Practical 11

### Total Sales by Region

```sql
SELECT region,
       SUM(sales_amount) AS total_sales
FROM Sales
GROUP BY region;
```

### Expected Output

| region | total_sales |
| ------ | ----------- |
| North  | 8000        |
| South  | 9000        |
| East   | 8000        |

---

## Practical 12

### Average Score by Class

```sql
SELECT class,
       AVG(score) AS average_score
FROM Students
GROUP BY class;
```

### Expected Output

| class | average_score |
| ----- | ------------- |
| A     | 90            |
| B     | 72.5          |

---

## Practical 13

### Salespersons with Total Sales Greater Than ₹8,000

```sql
SELECT salesperson,
       SUM(sales_amount) AS total_sales
FROM Sales
GROUP BY salesperson
HAVING SUM(sales_amount) > 8000;
```

### Expected Output

| salesperson | total_sales |
| ----------- | ----------- |
| Bob         | 9000        |

---

## Practical 14

### Students Appearing More Than Once

```sql
SELECT student_name,
       COUNT(*) AS appearances
FROM Students
GROUP BY student_name
HAVING COUNT(*) > 1;
```

---

## Practical 15

### Employees Earning Above Average Salary

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

# ⭐ Bonus Challenge Solution

### Customers with Total Orders Greater Than ₹400

```sql
SELECT customer_id,
       SUM(order_amount) AS total_orders
FROM Orders
GROUP BY customer_id
HAVING SUM(order_amount) > 400;
```

### Expected Output

| customer_id | total_orders |
| ----------- | ------------ |
| 2           | 600          |
| 3           | 500          |

---

# 📊 Assessment Performance Evaluation

| Score    | Level               |
| -------- | ------------------- |
| 27 – 30  | SQL Master 🌟       |
| 23 – 26  | SQL Advanced 🚀     |
| 18 – 22  | SQL Intermediate 📚 |
| 12 – 17  | SQL Beginner 🔰     |
| Below 12 | Needs Revision 📖   |

---


# 🏆 Day 10 Completion

Congratulations! 🎉

You have successfully completed the first milestone assessment of the 30 Days of SQL Challenge. If you can confidently solve most of these questions without referring to notes, you are ready to move on to advanced SQL concepts.

---

**Progress Status:** Day 10 Assessment Completed ✅
