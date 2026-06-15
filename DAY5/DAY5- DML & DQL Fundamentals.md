# 🚀 30 Days of SQL – Day 5: DML & DQL Fundamentals (INSERT, UPDATE, DELETE & SELECT)

Welcome to **Day 5** of the **30 Days of SQL Challenge**!

In Day 4, you learned about SQL command categories and explored **Data Definition Language (DDL)** commands such as CREATE, ALTER, DROP, TRUNCATE, and RENAME.

Today, we'll focus on two of the most important SQL categories:

- **DML (Data Manipulation Language)** – Used to manage and modify data.
- **DQL (Data Query Language)** – Used to retrieve data.

Think of it this way:

- DDL creates the library building and shelves.
- DML adds, updates, and removes books.
- DQL helps visitors find books.

---

# 📚 Table of Contents

1. What is DML?
2. Why is DML Important?
3. DML Commands Overview
4. INSERT Statement
5. INSERT into Specific Columns
6. INSERT Multiple Records
7. INSERT INTO ... SELECT
8. UPDATE Statement
9. DELETE Statement
10. What is DQL?
11. Why is DQL Important?
12. SELECT Statement
13. Retrieving Specific Columns
14. Retrieving All Columns
15. DML vs DQL
16. Practice Exercises
17. Key Takeaways
18. Day 5 Summary

---

# 1️⃣ What is DML?

**DML (Data Manipulation Language)** consists of commands used to manipulate the data stored inside tables.

While DDL focuses on creating database structures, DML focuses on managing the records inside those structures.

---

## 📖 Library Analogy

Imagine a library:

| Activity | SQL Command |
|-----------|------------|
| Add a new book | INSERT |
| Update book details | UPDATE |
| Remove a book | DELETE |

These operations represent DML.

---

# 2️⃣ Why is DML Important?

Without DML:

❌ New records cannot be added

❌ Existing information cannot be updated

❌ Incorrect records cannot be removed

With DML:

✅ Databases stay updated

✅ Information remains accurate

✅ Records can be maintained efficiently

✅ Businesses can manage data effectively

---

# 3️⃣ DML Commands Overview

| Command | Purpose |
|----------|----------|
| INSERT | Add new records |
| UPDATE | Modify existing records |
| DELETE | Remove records |

---

# 4️⃣ INSERT Statement

The **INSERT** statement is used to add new records to a table.

## Syntax

```sql
INSERT INTO table_name
VALUES (...);
```

## Example

```sql
INSERT INTO Students
VALUES
(101, 'Harry', 23, 'Mumbai');
```

### Output

| student_id | student_name | age | city |
|------------|-------------|-----|------|
| 101 | Harry | 23 | Mumbai |

---

# 5️⃣ INSERT into Specific Columns

Sometimes you don't want to provide values for every column.

## Syntax

```sql
INSERT INTO table_name
(column1, column2)
VALUES
(value1, value2);
```

## Example

```sql
INSERT INTO Students
(student_id, student_name)
VALUES
(102, 'Ron');
```

### Why Use It?

- When columns have DEFAULT values
- When using AUTO_INCREMENT
- When some fields are optional

---

# 6️⃣ INSERT Multiple Records

Multiple records can be inserted using a single query.

## Example

```sql
INSERT INTO Students
(student_id, student_name, age)
VALUES
(103, 'Sam', 24),
(104, 'Riya', 22),
(105, 'Aman', 25);
```

## Benefits

✅ Faster execution

✅ Better performance

✅ Fewer SQL statements

---

# 7️⃣ INSERT INTO ... SELECT

Used to copy data from one table into another.

## Syntax

```sql
INSERT INTO target_table
SELECT *
FROM source_table;
```

## Example

```sql
INSERT INTO ArchivedStudents
SELECT *
FROM Students;
```

### Use Cases

- Creating backups
- Archiving records
- Migrating data

---

# 8️⃣ UPDATE Statement

The **UPDATE** statement modifies existing records.

## Syntax

```sql
UPDATE table_name
SET column_name = value
WHERE condition;
```

## Example

```sql
UPDATE Students
SET city = 'Pune'
WHERE student_id = 101;
```

### Before

| student_id | city |
|------------|------|
| 101 | Mumbai |

### After

| student_id | city |
|------------|------|
| 101 | Pune |

---

## ⚠️ Important

Without a WHERE clause:

```sql
UPDATE Students
SET city = 'Delhi';
```

Every row in the table will be updated.

---

# 9️⃣ DELETE Statement

The **DELETE** statement removes records from a table.

## Syntax

```sql
DELETE FROM table_name
WHERE condition;
```

## Example

```sql
DELETE FROM Students
WHERE student_id = 105;
```

### Before

| student_id |
|------------|
| 101 |
| 102 |
| 105 |

### After

| student_id |
|------------|
| 101 |
| 102 |

---

## ⚠️ Important

Without a WHERE clause:

```sql
DELETE FROM Students;
```

All records will be removed from the table.

# 🔄 DELETE vs TRUNCATE

Both DELETE and TRUNCATE are used to remove data from a table, but they work differently.

## Comparison Table

| Feature | DELETE | TRUNCATE |
|----------|----------|----------|
| Category | DML | DDL |
| Removes | Selected rows or all rows | All rows |
| WHERE Clause | ✅ Supported | ❌ Not Supported |
| Speed | Slower | Faster |
| Logging | Row-by-row logging | Minimal logging |
| Table Structure | Remains unchanged | Remains unchanged |
| AUTO_INCREMENT Counter | Usually unchanged | Usually reset |
| Trigger Execution | ✅ Executes triggers | ❌ Typically skips triggers |

---

# 🔟 What is DQL?

**DQL (Data Query Language)** is used to retrieve data from databases.

The primary command in DQL is:

```sql
SELECT
```

---

# 1️⃣1️⃣ Why is DQL Important?

Every report, dashboard, website, and business application retrieves data using SELECT statements.

Examples:

- Student Records
- Employee Reports
- Customer Information
- Sales Dashboards
- Analytics Reports

All start with SELECT.

---

# 1️⃣2️⃣ SELECT Statement

The **SELECT** statement retrieves data from one or more tables.

## Syntax

```sql
SELECT column_name
FROM table_name;
```

## Example

```sql
SELECT student_name
FROM Students;
```

### Output

| student_name |
|-------------|
| Harry |
| Ron |
| Sam |

---

# 1️⃣3️⃣ Retrieving Specific Columns

```sql
SELECT student_name, city
FROM Students;
```

### Output

| student_name | city |
|-------------|------|
| Harry | Pune |
| Ron | Mumbai |

---

# 1️⃣4️⃣ Retrieving All Columns

Use `*` to retrieve all columns.

```sql
SELECT *
FROM Students;
```

### Output

| student_id | student_name | age | city |
|------------|-------------|-----|------|
| 101 | Harry | 23 | Pune |
| 102 | Ron | 22 | Mumbai |

---

# 📊 DML vs DQL

| Command | Category | Purpose |
|----------|----------|----------|
| INSERT | DML | Add records |
| UPDATE | DML | Modify records |
| DELETE | DML | Remove records |
| SELECT | DQL | Retrieve records |

---

# 📝 Practice Exercises

## Exercise 1

Create an Employees table and insert 5 records.

---

## Exercise 2

Insert multiple employee records using a single INSERT statement.

---

## Exercise 3

Update an employee's department.

---

## Exercise 4

Delete an employee using employee_id.

---

## Exercise 5

Display:

- All employee records
- Employee names only
- Employee names and departments

using SELECT queries.

---

## Exercise 6

Create a backup table and copy data using:

```sql
INSERT INTO BackupEmployees
SELECT *
FROM Employees;
```

---

# 🎯 Key Takeaways

✅ Learned the purpose of DML

✅ Understood INSERT operations

✅ Learned INSERT INTO ... SELECT

✅ Understood UPDATE operations

✅ Understood DELETE operations

✅ Learned the purpose of DQL

✅ Retrieved data using SELECT

✅ Distinguished between DML and DQL

---

# 📖 Day 5 Summary

Today, you learned how SQL works with actual data stored inside tables. DML commands allow you to add, update, and delete records, while DQL enables you to retrieve information whenever needed. Together, these commands form the foundation of everyday database operations and are heavily used by developers, analysts, and database administrators.

---

## 🚀 Coming Up Next: Day 6 – Filtering Data with WHERE

You'll learn how to retrieve only the data you need by applying conditions and filters to SELECT queries.

```sql
WHERE
AND
OR
NOT
IN
BETWEEN
LIKE
```
---
## **Progress Status:** Day 5 Completed ✅
---
[PREVIOUS: DAY4](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/8a8aa07f01de27acddb451a3cfe8d9e019c2bff7/DAY4/DAY4-SQL%20Command%20Categories%20%26%20Introduction%20to%20DDL.md)👆\
[NEXT: DAY6](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/8a8aa07f01de27acddb451a3cfe8d9e019c2bff7/DAY6/DAY6-Filtering%20Data%20with%20WHERE%20Clause.md)👇
