# 🚀 30 Days of SQL – Day 11: SQL Joins Fundamentals

Welcome to **Day 11** of the **30 Days of SQL Challenge**!

In previous lessons, we worked with individual tables. However, in real-world database systems, data is rarely stored in a single table.

For example:

* Customer details are stored in a Customers table.
* Orders are stored in an Orders table.
* Products are stored in a Products table.

To retrieve meaningful information from multiple tables, SQL uses **Joins**.

Today, you'll learn:

* What Joins are
* Why Joins are required
* Why tables are joined using related columns
* Types of Joins
* Real-world examples
* Join visualizations
* Practice Exercises

---

# 📚 Table of Contents

1. What is a Join?
2. Why Are Joins Required?
3. Understanding Relationships Before Joins
4. Why Are Tables Joined Using Common Columns?
5. Why Not Join Random Columns?
6. Types of SQL Joins
7. INNER JOIN
8. LEFT JOIN
9. RIGHT JOIN
10. FULL OUTER JOIN
11. CROSS JOIN
12. SELF JOIN
13. Join Comparison Table
14. Real-World Use Cases
15. Practice Exercises
16. Key Takeaways
17. Day 11 Summary

---

# 1️⃣ What is a Join?

A Join is an SQL operation used to combine data from two or more tables based on a common column.

Think of Joins as bridges connecting related tables.

Without joins:

```text
Customers Table
Orders Table

Remain Separate
```

With joins:

```text
Customers + Orders

Become Meaningful Information
```

Example:

Instead of:

| customer_id |
| ----------- |
| 101         |

We can display:

| customer_name | order_amount |
| ------------- | ------------ |
| Diya          | ₹5000        |

---

# 2️⃣ Why Are Joins Required?

Imagine an online shopping application.

### Customers Table

| customer_id | customer_name |
| ----------- | ------------- |
| 101         | Diya          |
| 102         | Harry          |

### Orders Table

| order_id | customer_id | amount |
| -------- | ----------- | ------ |
| 1        | 101         | 5000   |
| 2        | 102         | 3000   |

Questions management may ask:

* Which customer placed which order?
* What is the total spending of each customer?
* Which customers haven't placed any orders?

These answers require combining tables.

That's why Joins exist.

---

# 3️⃣ Understanding Relationships Before Joins

Joins work because tables are connected through relationships.

### Example

Customers

| customer_id | customer_name |
| ----------- | ------------- |
| 101         | Diya          |
| 102         | Harry          |

Orders

| order_id | customer_id |
| -------- | ----------- |
| 1        | 101         |
| 2        | 101         |
| 3        | 102         |

Relationship:

```text
One Customer
Can Have
Many Orders
```

This is a:

```text
One-to-Many Relationship
```

---

# 4️⃣ Why Are Tables Joined Using Common Columns?

Many beginners ask:

> Why do we join using IDs and not Names?

Consider:

### Customers

| customer_id | customer_name |
| ----------- | ------------- |
| 101         | John          |
| 102         | John          |

Two customers can have the same name.

But:

```text
customer_id
```

is always unique.

Therefore joins are usually performed using:

* Primary Keys
* Foreign Keys

Example:

```sql
SELECT *
FROM Customers c
INNER JOIN Orders o
ON c.customer_id = o.customer_id;
```

---

# 5️⃣ Why Not Join Random Columns?

Suppose:

```sql
ON customer_name = order_amount
```

This makes no logical sense.

Joins should always be based on:

✅ Related data

✅ Common business meaning

✅ Primary-Foreign Key relationships

---

# 6️⃣ Types of SQL Joins

SQL provides several types of joins.

| Join Type       | Purpose                      |
| --------------- | ---------------------------- |
| INNER JOIN      | Matching records only        |
| LEFT JOIN       | All left records             |
| RIGHT JOIN      | All right records            |
| FULL OUTER JOIN | All records from both tables |
| CROSS JOIN      | Every possible combination   |
| SELF JOIN       | Join table with itself       |



---

# Sample Data

### Customers

| customer_id | customer_name |
| ----------- | ------------- |
| 101         | Diya          |
| 102         | Harry          |
| 103         | Ron           |

### Orders

| order_id | customer_id |
| -------- | ----------- |
| 1        | 101         |
| 2        | 102         |
| 3        | 104         |

---

# 7️⃣ INNER JOIN

Returns only matching records from both tables.

## Syntax

```sql
SELECT *
FROM Customers c
INNER JOIN Orders o
ON c.customer_id = o.customer_id;
```

---

### Result

| customer_name | order_id |
| ------------- | -------- |
| Diya          | 1        |
| Harry          | 2        |

---

### Visualization

```text
Customers ∩ Orders

Only Common Data
```

---

### Use Cases

✅ Customers with orders

✅ Students with enrollments

✅ Employees with departments

---

# 8️⃣ LEFT JOIN

Returns:

```text
All Left Table Records
+
Matching Right Table Records
```

---

## Syntax

```sql
SELECT *
FROM Customers c
LEFT JOIN Orders o
ON c.customer_id = o.customer_id;
```

---

### Result

| customer_name | order_id |
| ------------- | -------- |
| Diya          | 1        |
| Harry          | 2        |
| Ron           | NULL     |

---

### Use Cases

✅ Customers without orders

✅ Students without courses

---

# 9️⃣ RIGHT JOIN

Returns:

```text
All Right Table Records
+
Matching Left Table Records
```

---

## Syntax

```sql
SELECT *
FROM Customers c
RIGHT JOIN Orders o
ON c.customer_id = o.customer_id;
```

---

### Result

| customer_name | order_id |
| ------------- | -------- |
| Diya          | 1        |
| Harry          | 2        |
| NULL          | 3        |

---

### Use Cases

✅ Orders without customers

✅ Detect orphan records

---

# 🔟 FULL OUTER JOIN

Returns all records from both tables.

---

## Syntax

```sql
SELECT *
FROM Customers c
FULL OUTER JOIN Orders o
ON c.customer_id = o.customer_id;
```

---

### Result

| customer_name | order_id |
| ------------- | -------- |
| Diya          | 1        |
| Harry          | 2        |
| Ron           | NULL     |
| NULL          | 3        |

---

### Use Cases

✅ Data reconciliation

✅ Data auditing

✅ Migration validation

---

# 1️⃣1️⃣ CROSS JOIN

Returns every possible combination.

---

### Example

Colors

| color |
| ----- |
| Red   |
| Blue  |

Sizes

| size |
| ---- |
| S    |
| M    |

---

### Query

```sql
SELECT *
FROM Colors
CROSS JOIN Sizes;
```

---

### Output

| color | size |
| ----- | ---- |
| Red   | S    |
| Red   | M    |
| Blue  | S    |
| Blue  | M    |

---

### Formula

```text
Rows Returned

=
Rows(Table A)
×
Rows(Table B)
```

---

### Use Cases

✅ Product combinations

✅ Scheduling systems

✅ Test data generation

---

# 1️⃣2️⃣ SELF JOIN

A table joined with itself.

---

### Employees Table

| employee_id | employee_name | manager_id |
| ----------- | ------------- | ---------- |
| 1           | John          | NULL       |
| 2           | Sarah         | 1          |
| 3           | Mike          | 1          |

---

### Query

```sql
SELECT
e.employee_name,
m.employee_name AS manager_name
FROM Employees e
LEFT JOIN Employees m
ON e.manager_id = m.employee_id;
```

---

### Result

| Employee | Manager |
| -------- | ------- |
| Sarah    | John    |
| Mike     | John    |

---

### Use Cases

✅ Employee hierarchy

✅ Organization structures

✅ Category hierarchy

---

# 1️⃣3️⃣ Join Comparison Table

| Join       | Returns                   |
| ---------- | ------------------------- |
| INNER      | Matching rows only        |
| LEFT       | All left rows             |
| RIGHT      | All right rows            |
| FULL OUTER | All rows from both tables |
| CROSS      | Every combination         |
| SELF       | Same table relationship   |

<img width="647" height="432" alt="image" src="https://github.com/user-attachments/assets/f1087d57-3ae4-4020-bdee-b9c6fa444263" />


---

# 1️⃣4️⃣ Real-World Use Cases

### E-Commerce

Customers + Orders

<img width="244" height="171" alt="image" src="https://github.com/user-attachments/assets/1773e3f0-ee35-4679-88e4-8b3c2ab4c85a" />

---

### Banking

Customers + Accounts

<img width="233" height="175" alt="image" src="https://github.com/user-attachments/assets/94acbea5-5b83-401c-8bc3-86783856f47f" />

---

### Education

Students + Courses

<img width="248" height="172" alt="image" src="https://github.com/user-attachments/assets/29569c95-739a-4555-be51-86267db689ce" />

---

### Hospital

Patients + Appointments

<img width="238" height="168" alt="image" src="https://github.com/user-attachments/assets/adce315b-5c5c-4f53-9ae6-96984128469b" />

---

### HR Systems

Employees + Departments

<img width="233" height="167" alt="image" src="https://github.com/user-attachments/assets/a5ef4207-9288-4228-9a14-3e3ec816e813" />

---

### CRM Supports

Customers + Support tickets

<img width="242" height="164" alt="image" src="https://github.com/user-attachments/assets/6e8830c9-39d8-4ff2-a198-f3f7ee90c090" />

---

# 📝 Practice Exercises

### Exercise 1

Create Customers and Orders tables.

---

### Exercise 2

Insert sample records.

---

### Exercise 3

Perform an INNER JOIN.

---

### Exercise 4

Perform a LEFT JOIN.

---

### Exercise 5

Perform a RIGHT JOIN.

---

### Exercise 6

Perform a FULL OUTER JOIN.

---

### Exercise 7

Create a CROSS JOIN example.

---

### Exercise 8

Create an Employee-Manager hierarchy using SELF JOIN.

---


# 🎯 Key Takeaways

✅ Understood SQL Joins

✅ Learned why joins are required

✅ Understood Primary Key–Foreign Key relationships

✅ Learned INNER JOIN

✅ Learned LEFT JOIN

✅ Learned RIGHT JOIN

✅ Learned FULL OUTER JOIN

✅ Learned CROSS JOIN

✅ Learned SELF JOIN

✅ Solved practical join problems

---

# 📖 Day 11 Summary

Today, you learned one of the most important concepts in SQL—Joins. Since relational databases store information across multiple related tables, joins allow us to retrieve meaningful business information by combining data logically.

Understanding joins is essential for reporting, analytics, dashboards, and real-world database development.

---

## 🚀 Coming Up Next: Day 12 – Advanced Joins & Set Operators

You'll learn:

```sql
UNION
UNION ALL
INTERSECT
EXCEPT
MINUS
```

and understand how to combine results from multiple queries efficiently.

**Progress Status:** Day 11 Completed ✅
