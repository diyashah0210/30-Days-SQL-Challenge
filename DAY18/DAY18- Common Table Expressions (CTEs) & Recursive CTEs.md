# 🚀 30 Days of SQL – Day 18: Common Table Expressions (CTEs) & Recursive CTEs

Welcome to **Day 18** of the **30 Days of SQL Challenge**!

Today, we'll explore **Common Table Expressions (CTEs)** and **Recursive CTEs**, one of the most powerful SQL features for writing clean, modular, and hierarchical queries.

CTEs help simplify complex SQL statements, improve readability, and make query maintenance much easier.

---

# 📚 Table of Contents

1. Introduction to CTEs
2. Why Do We Need CTEs?
3. Syntax of a CTE
4. CTE vs Subquery
5. Single CTE
6. Multiple CTEs
7. Using CTEs with Joins
8. Using CTEs with Aggregate Functions
9. Recursive CTEs
10. Anchor Query and Recursive Query
11. Generating Number Sequences
12. Hierarchical Data
13. Organizational Charts
14. Parent-Child Relationships
15. Tree Structures
16. Bill of Materials (BOM)
17. Real-World Use Cases
18. Common Mistakes
19. Practice Exercises
20. Key Takeaways
21. Day 18 Summary

---

# 1️⃣ Introduction to CTEs

A **Common Table Expression (CTE)** is a temporary named result set that exists only for the duration of a query.

Think of it as a temporary table created within your SQL statement.

### Benefits of CTEs

✅ Improves readability

✅ Simplifies complex queries

✅ Makes debugging easier

✅ Encourages modular query design

✅ Helps organize large SQL statements

---

# 2️⃣ Why Do We Need CTEs?

As SQL queries become larger and more complex, nested subqueries can become difficult to read and maintain.

### Without a CTE

```sql
SELECT *
FROM
(
    SELECT department,
           AVG(salary) AS avg_salary
    FROM Employees
    GROUP BY department
) AS DepartmentData
WHERE avg_salary > 60000;
```

### Using a CTE

```sql
WITH DepartmentSalary AS
(
    SELECT department,
           AVG(salary) AS avg_salary
    FROM Employees
    GROUP BY department
)
SELECT *
FROM DepartmentSalary
WHERE avg_salary > 60000;
```

The second approach is cleaner and easier to understand.

---

# 3️⃣ Syntax of a CTE

```sql
WITH cte_name AS
(
    SELECT column1,
           column2
    FROM table_name
)
SELECT *
FROM cte_name;
```

### Components

| Component | Description |
|------------|------------|
| WITH | Begins the CTE definition |
| cte_name | Name of the temporary result set |
| AS | Defines the query |
| Main Query | Uses the CTE like a table |

---

# 4️⃣ CTE vs Subquery

| Feature | CTE | Subquery |
|----------|------|----------|
| Readability | High | Moderate |
| Reusability | Yes | Limited |
| Maintenance | Easy | Difficult |
| Debugging | Easier | Harder |
| Best For | Complex Queries | Small Queries |

---

# 5️⃣ Single CTE

### Example

```sql
WITH HighSalaryEmployees AS
(
    SELECT *
    FROM Employees
    WHERE salary > 70000
)
SELECT *
FROM HighSalaryEmployees;
```

### Output

Returns all employees earning more than ₹70,000.

---

# 6️⃣ Multiple CTEs

You can define multiple CTEs in a single query.

```sql
WITH DepartmentAverage AS
(
    SELECT department,
           AVG(salary) AS avg_salary
    FROM Employees
    GROUP BY department
),
EmployeeCount AS
(
    SELECT department,
           COUNT(*) AS total_employees
    FROM Employees
    GROUP BY department
)
SELECT *
FROM DepartmentAverage;
```

---

# 7️⃣ Using CTEs with Joins

### Example

```sql
WITH EmployeeDepartment AS
(
    SELECT
        e.employee_name,
        d.department_name
    FROM Employees e
    INNER JOIN Departments d
        ON e.department_id = d.department_id
)
SELECT *
FROM EmployeeDepartment;
```

### Use Cases

- Employee Reports
- Customer Orders
- Product Categories

---

# 8️⃣ Using CTEs with Aggregate Functions

### Example

```sql
WITH DepartmentSalary AS
(
    SELECT
        department,
        AVG(salary) AS avg_salary
    FROM Employees
    GROUP BY department
)
SELECT *
FROM DepartmentSalary;
```

### Output

Average salary by department.

---

# 9️⃣ Recursive CTEs

A **Recursive CTE** is a CTE that references itself.

It is commonly used for:

- Hierarchical Data
- Organizational Structures
- Folder Systems
- Product Categories
- Tree Traversal

---

# 🔟 Anchor Query and Recursive Query

A Recursive CTE consists of two parts:

## Anchor Query

The starting point.

## Recursive Query

The query that repeatedly references itself.

### Syntax

```sql
WITH RECURSIVE cte_name AS
(
    Anchor Query

    UNION ALL

    Recursive Query
)
SELECT *
FROM cte_name;
```

---

# 1️⃣1️⃣ Generating Number Sequences

Generate numbers from 1 to 10.

```sql
WITH RECURSIVE Numbers AS
(
    SELECT 1 AS num

    UNION ALL

    SELECT num + 1
    FROM Numbers
    WHERE num < 10
)
SELECT *
FROM Numbers;
```

### Output

```text
1
2
3
4
5
6
7
8
9
10
```

---

# 1️⃣2️⃣ Hierarchical Data

Hierarchical data represents relationships where records are connected in levels.

### Example

| Employee | Manager |
|------------|----------|
| CEO | NULL |
| Manager A | CEO |
| Manager B | CEO |
| Employee 1 | Manager A |
| Employee 2 | Manager B |

---

# 1️⃣3️⃣ Organizational Charts

### Example

```sql
WITH RECURSIVE OrgChart AS
(
    SELECT
        employee_id,
        employee_name,
        manager_id
    FROM Employees
    WHERE manager_id IS NULL

    UNION ALL

    SELECT
        e.employee_id,
        e.employee_name,
        e.manager_id
    FROM Employees e
    INNER JOIN OrgChart o
        ON e.manager_id = o.employee_id
)
SELECT *
FROM OrgChart;
```

---

# 1️⃣4️⃣ Parent-Child Relationships

Common examples include:

- Country → State → City
- Department → Team
- Category → Subcategory
- Manager → Employee

Recursive CTEs help traverse these structures efficiently.

---

# 1️⃣5️⃣ Tree Structures

Tree structures are widely used in:

### File Systems

```text
Root
├── Documents
│   ├── Reports
│   └── Notes
└── Downloads
```

### Other Examples

- Product Categories
- Website Menus
- Comment Threads
- Family Trees

---

# 1️⃣6️⃣ Bill of Materials (BOM)

Manufacturing systems use recursive queries to identify all components required to build a product.

### Example

```text
Car
├── Engine
├── Battery
├── Wheels
├── Seats
└── Steering Wheel
```

Recursive CTEs can retrieve every component and sub-component.

---

# 1️⃣7️⃣ Real-World Use Cases

## HR Systems

Employee reporting hierarchy.

## Banking

Branch and regional office hierarchy.

## E-Commerce

Product category trees.

## Education

Course prerequisite chains.

## Manufacturing

Bill of Materials tracking.

## Operating Systems

Folder and file navigation.

---

# 1️⃣8️⃣ Common Mistakes

### ❌ Forgetting UNION ALL

Recursive CTEs generally require `UNION ALL`.

### ❌ Missing Termination Condition

```sql
WHERE num < 10
```

Without a stopping condition, recursion may become infinite.

### ❌ Using Recursive CTEs for Simple Problems

Not every problem requires recursion.

### ❌ Incorrect Join Conditions

Can create duplicate or missing records.

---

# 📝 Practice Exercises

### Exercise 1

Create a CTE showing employees earning above ₹50,000.

### Exercise 2

Calculate average salary by department using a CTE.

### Exercise 3

Create multiple CTEs in a single query.

### Exercise 4

Use a CTE with an INNER JOIN.

### Exercise 5

Generate numbers from 1 to 20 using recursion.

### Exercise 6

Generate even numbers using a Recursive CTE.

### Exercise 7

Generate odd numbers using a Recursive CTE.

### Exercise 8

Build an employee hierarchy.

### Exercise 9

Display manager-employee relationships.

### Exercise 10

Create a product category hierarchy.

### Exercise 11

Find all descendants of a category.

### Exercise 12

Build an organizational chart.

### Exercise 13

Create a file-system hierarchy.

### Exercise 14

Build a Bill of Materials query.

### Exercise 15

Create a complete recursive hierarchy report.

---

# 🎯 Key Takeaways

✅ CTEs improve readability and maintainability.

✅ CTEs act as temporary result sets.

✅ Multiple CTEs can exist in one query.

✅ CTEs work seamlessly with Joins and Aggregations.

✅ Recursive CTEs reference themselves.

✅ Recursive CTEs consist of:
- Anchor Query
- Recursive Query

✅ Recursive CTEs are ideal for hierarchical data.

✅ Common applications include:
- Employee Hierarchies
- Folder Structures
- Product Categories
- Organizational Charts

---

# 📖 Day 18 Summary

Today, you learned how Common Table Expressions (CTEs) simplify complex SQL queries and make them easier to read and maintain.

You also explored Recursive CTEs, which enable SQL to work with hierarchical and tree-like structures such as organizational charts, folder systems, product categories, and Bills of Materials.

Mastering CTEs is an essential step toward writing professional, scalable, and interview-ready SQL queries.

---

## 🚀 Coming Up Next: Day 19 – Views

Topics Covered:

- What are Views?
- Creating Views
- Updating Views
- Advantages of Views
- Materialized Views
- Security Through Views
- Real-World Applications

## Progress Status: Day 18 Completed ✅
---

[PREVIOUS: DAY17](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/45b2d2dfb4dd18bc1c814ddd126d8d203761fd09/DAY17/DAY17-%20Window%20Functions.md.md)👆\
[NEXT: DAY19]()👇
