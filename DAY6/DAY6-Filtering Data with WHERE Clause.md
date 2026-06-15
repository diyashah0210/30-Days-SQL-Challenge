# 🚀 30 Days of SQL – Day 6: Filtering Data with WHERE Clause

Welcome to **Day 6** of the **30 Days of SQL Challenge**!

In previous lessons, we learned how to create databases, tables, manipulate records, and retrieve data using the SELECT statement.

However, in real-world databases, retrieving every record is rarely useful. Businesses often need specific information such as:

* Students above a certain age
* Employees from a particular department
* Customers from specific cities
* Products within a price range

This is where **SQL Filtering** becomes essential.

Today, you'll learn how to retrieve exactly the data you need using the WHERE clause and various filtering operators.

---

# 📚 Table of Contents

1. Why Data Filtering is Important
2. Understanding the WHERE Clause
3. Conditional Filtering (Comparison Operators)
4. AND Operator
5. OR Operator
6. NOT Operator
7. IN Operator
8. BETWEEN Operator
9. LIKE Operator
10. Wildcards in LIKE
11. Combining Multiple Conditions
12. Operator Precedence
13. Filtering with NULL Values
14. Practice Exercises
15. Key Takeaways
16. Day 6 Summary

---

# 1️⃣ Why Data Filtering is Important

Imagine a library containing 50,000 books.

A visitor asks:

> Show me Science books published after 2020.

Would you display all 50,000 books?

Of course not.

Instead, you would apply filters.

Similarly, databases often contain thousands or millions of records. SQL filtering allows us to retrieve only the records that satisfy specific conditions.

### Benefits of Filtering

✅ Faster Data Retrieval

✅ Better Data Analysis

✅ Improved Report Generation

✅ Reduced Data Processing

---

# 2️⃣ Understanding the WHERE Clause

The **WHERE** clause is used to filter records based on specific conditions.

## Syntax

```sql
SELECT column_name
FROM table_name
WHERE condition;
```

## Example

```sql
SELECT *
FROM Students
WHERE age > 20;
```

### Output

Only students whose age is greater than 20 will be displayed.

---

# 3️⃣ Conditional Filtering (Comparison Operators)

Comparison operators help compare values inside conditions.

| Operator | Meaning                  |
| -------- | ------------------------ |
| =        | Equal To                 |
| >        | Greater Than             |
| <        | Less Than                |
| >=       | Greater Than or Equal To |
| <=       | Less Than or Equal To    |
| <>       | Not Equal To             |
| !=       | Not Equal To             |

## Examples

### Equal To

```sql
SELECT *
FROM Students
WHERE city = 'Mumbai';
```

### Greater Than

```sql
SELECT *
FROM Students
WHERE age > 18;
```

### Not Equal To

```sql
SELECT *
FROM Students
WHERE city <> 'Delhi';
```

---

# 4️⃣ AND Operator

The **AND** operator returns records only when all conditions are TRUE.

## Syntax

```sql
SELECT *
FROM Students
WHERE city = 'Mumbai'
AND age > 20;
```

### Truth Table

| Condition A | Condition B | Result |
| ----------- | ----------- | ------ |
| TRUE        | TRUE        | TRUE   |
| TRUE        | FALSE       | FALSE  |
| FALSE       | TRUE        | FALSE  |
| FALSE       | FALSE       | FALSE  |

### Example

```sql
SELECT *
FROM Students
WHERE city = 'Mumbai'
AND age > 20;
```

Only students who satisfy both conditions will be displayed.

---

# 5️⃣ OR Operator

The **OR** operator returns records when at least one condition is TRUE.

## Syntax

```sql
SELECT *
FROM Students
WHERE city = 'Mumbai'
OR city = 'Pune';
```

### Truth Table

| Condition A | Condition B | Result |
| ----------- | ----------- | ------ |
| TRUE        | TRUE        | TRUE   |
| TRUE        | FALSE       | TRUE   |
| FALSE       | TRUE        | TRUE   |
| FALSE       | FALSE       | FALSE  |

### Example

```sql
SELECT *
FROM Students
WHERE city = 'Mumbai'
OR city = 'Pune';
```

Students from either city will be displayed.

---

# 6️⃣ NOT Operator

The **NOT** operator reverses a condition.

## Syntax

```sql
SELECT *
FROM Students
WHERE NOT city = 'Mumbai';
```

### Truth Table

| Condition | Result |
| --------- | ------ |
| TRUE      | FALSE  |
| FALSE     | TRUE   |

### Example

```sql
SELECT *
FROM Students
WHERE NOT city = 'Mumbai';
```

All students except those from Mumbai will be displayed.

---

# 7️⃣ IN Operator

The **IN** operator is used when checking multiple values.

Instead of writing multiple OR conditions:

```sql
SELECT *
FROM Students
WHERE city = 'Mumbai'
OR city = 'Pune'
OR city = 'Delhi';
```

Use:

```sql
SELECT *
FROM Students
WHERE city IN ('Mumbai','Pune','Delhi');
```

### Benefits

✅ Cleaner Queries

✅ Easier Maintenance

✅ Better Readability

---

# 8️⃣ BETWEEN Operator

The **BETWEEN** operator is used to filter values within a range.

## Syntax

```sql
SELECT *
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```

## Example

```sql
SELECT *
FROM Students
WHERE age BETWEEN 18 AND 25;
```

### Output

Displays students whose age lies between 18 and 25.

---

# 9️⃣ LIKE Operator

The **LIKE** operator is used for pattern matching.

## Syntax

```sql
SELECT *
FROM Students
WHERE student_name LIKE 'D%';
```

### Example

```sql
SELECT *
FROM Students
WHERE student_name LIKE 'A%';
```

Displays names starting with A.

---

# 🔟 Wildcards in LIKE

Wildcards make pattern searching more powerful.

| Wildcard | Meaning                  |
| -------- | ------------------------ |
| %        | Any number of characters |
| _        | Exactly one character    |

## Starts With

```sql
SELECT *
FROM Students
WHERE student_name LIKE 'D%';
```

Matches:

```text
Diya
Divya
Dhruv
```

---

## Ends With

```sql
SELECT *
FROM Students
WHERE student_name LIKE '%a';
```

Matches:

```text
Diya
Arya
Riya
```

---

## Contains

```sql
SELECT *
FROM Students
WHERE student_name LIKE '%iy%';
```

Matches:

```text
Diya
```

---

## Single Character

```sql
SELECT *
FROM Students
WHERE student_name LIKE '_iya';
```

Matches:

```text
Diya
Riya
Siya
```

---

# 1️⃣1️⃣ Combining Multiple Conditions

Multiple filtering operators can be combined together.

## Example

```sql
SELECT *
FROM Students
WHERE city = 'Mumbai'
AND age BETWEEN 18 AND 25;
```

---

## Example

```sql
SELECT *
FROM Students
WHERE city IN ('Mumbai','Pune')
AND student_name LIKE 'D%';
```

---

# 1️⃣2️⃣ Operator Precedence

SQL evaluates operators in the following order:

```text
1. NOT
2. AND
3. OR
```

## Example

```sql
SELECT *
FROM Students
WHERE city='Mumbai'
OR city='Pune'
AND age > 20;
```

The AND condition executes before OR.

### Best Practice

Use parentheses for clarity.

```sql
SELECT *
FROM Students
WHERE
(city='Mumbai'
OR city='Pune')
AND age > 20;
```

---

# 1️⃣3️⃣ Filtering with NULL Values

NULL represents missing or unknown data.

⚠️ NULL is not equal to 0.

⚠️ NULL is not an empty string.

---

## Finding NULL Values

```sql
SELECT *
FROM Students
WHERE phone_number IS NULL;
```

---

## Finding Non-NULL Values

```sql
SELECT *
FROM Students
WHERE phone_number IS NOT NULL;
```

---

### Why Use IS NULL?

The following query is incorrect:

```sql
SELECT *
FROM Students
WHERE phone_number = NULL;
```

Always use:

```sql
IS NULL
```

or

```sql
IS NOT NULL
```

---

# 📝 Practice Exercises

### Exercise 1

Display students whose age is greater than 18.

---

### Exercise 2

Display students from Mumbai and older than 20.

---

### Exercise 3

Display students from Mumbai or Pune.

---

### Exercise 4

Display students not from Delhi.

---

### Exercise 5

Display students whose age is between 18 and 25.

---

### Exercise 6

Display students whose names start with A.

---

### Exercise 7

Display students from Mumbai, Pune, and Delhi using IN.

---

### Exercise 8

Display students whose phone number is NULL.

---

### Exercise 9

Display students whose phone number is NOT NULL.

---

# 🎯 Key Takeaways

✅ Learned the purpose of filtering data

✅ Understood the WHERE clause

✅ Learned comparison operators

✅ Understood AND, OR, and NOT operators

✅ Learned truth tables for logical operators

✅ Used IN for multiple values

✅ Used BETWEEN for ranges

✅ Learned pattern matching using LIKE

✅ Understood wildcards (% and _)

✅ Learned operator precedence

✅ Filtered NULL and non-NULL values

---

# 📖 Day 6 Summary

Today, you learned how to filter records using SQL conditions. The WHERE clause is one of the most frequently used features in SQL because it allows you to retrieve only relevant data. You explored comparison operators, logical operators, pattern matching, range filtering, and handling NULL values.

These concepts form the foundation for writing powerful SQL queries used in reporting, analytics, and real-world database applications.

---

## 🚀 Coming Up Next: Day 7 – Sorting & Limiting Data

You'll learn:

```sql
ORDER BY
ASC
DESC
LIMIT
TOP
OFFSET
FETCH
```

and understand how to organize and restrict query results for reporting and analysis.

## Progress Status: Day 6 Completed ✅
---
[PREVIOUS: DAY5](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/35a26d2dc718241c83423e46bd4ae2f8ced26dcf/DAY5/DAY5-%20DML%20%26%20DQL%20Fundamentals.md)👆\
[NEXT: DAY7](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/35a26d2dc718241c83423e46bd4ae2f8ced26dcf/DAY7/DAY7-%20Sorting%20%26%20Limiting%20Data.md)👇
