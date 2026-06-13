# 🚀 30 Days of SQL – Day 8: SQL Functions

Welcome to **Day 8** of the **30 Days of SQL Challenge**!

In Day 7, you learned how to sort and limit data using:

* ORDER BY
* ASC
* DESC
* LIMIT
* TOP
* OFFSET
* FETCH

Today, we'll learn about **SQL Functions**, one of the most powerful features of SQL.

Functions help us perform calculations, manipulate text, format data, and generate meaningful insights from stored information without manually processing records.

---

# 📚 Table of Contents

1. What are SQL Functions?
2. Why are Functions Important?
3. Types of SQL Functions
4. Aggregate Functions: i. COUNT()
                        ii. SUM()
                        iii. AVG()
                        iv. MIN()
                        v. MAX()
5. String Functions: i. The Cleaner
                     ii. The Slicer
                     iii. The Glue
                     iv. The Location & Length
                     v. The "COUNTING" machine
7. Practice Exercises
8. Key Takeaways
9. Day 8 Summary

---

# 1️⃣ What are SQL Functions?

A function is a predefined operation that performs a specific task and returns a result.

Think of functions as ready-made tools provided by SQL.

Instead of manually calculating values, SQL functions perform the work automatically.

Functions help generate useful information quickly.

---

# 2️⃣ Why are Functions Important?

Without functions:

❌ Manual calculations

❌ Complex data processing

❌ Time-consuming analysis

With functions:

✅ Faster calculations

✅ Better reporting

✅ Easier analysis

✅ Improved productivity

---

# 3️⃣ Types of SQL Functions

SQL functions are broadly divided into:

# 4️⃣ Aggregate Functions

Operate on multiple rows and return a single value.

Suppose we have an Employees table:

| employee_id | employee_name | salary | dept |
| ----------- | ------------- | ------ | ---- |
| 1           | John          | 50000  |  HR  |
| 2           | Sarah         | 70000  |  HR  |
| 3           | Mike          | 60000  |  IT  |

Aggregate functions help generate summaries.

---

## I. COUNT()

COUNT() returns the total number of rows.

## Syntax

```sql
SELECT COUNT(*)
FROM Employees;
```

### Output

```text
3
```

---

## Count Specific Column

```sql
SELECT COUNT(employee_name)
FROM Employees;
```

### Output

```text
3
```
---

## Count Unique Values

```sql
SELECT COUNT(DISTINCT dept)
FROM Employees;
```
### Output

```text
2
```
---

# II. SUM()

SUM() calculates the total of numeric values.

## Syntax

```sql
SELECT SUM(salary)
FROM Employees;
```

### Output

```text
180000
```

---

# III. AVG()

AVG() calculates the average value.

## Syntax

```sql
SELECT AVG(salary)
FROM Employees;
```

### Output

```text
60000
```

---

# IV. MIN()

MIN() returns the smallest value.

## Syntax

```sql
SELECT MIN(salary)
FROM Employees;
```

### Output

```text
50000
```

---

# V. MAX()

MAX() returns the largest value.

## Syntax

```sql
SELECT MAX(salary)
FROM Employees;
```

### Output

```text
70000
```

---

# 5️⃣ String Functions

Used for text manipulation.
# 1.  THE CLEANERS: which includes
 UPPER()
 LOWER()
 TRIM()
 SUBSTRING()
 LEFT()
 RIGHT()

 ## I. UPPER()

Converts text to uppercase.

## Example

```sql
SELECT UPPER('Diya Shah');
```

### Output

```text
DIYA SHAH
```

---

## Using Column Values

```sql
SELECT UPPER(employee_name)
FROM Employees;
```

---

## II. LOWER()

Converts text to lowercase.

## Example

```sql
SELECT LOWER('DIYA SHAH');
```

### Output

```text
diya shah
```

---

## III. LENGTH()

Returns the number of characters.

## Example

```sql
SELECT LENGTH('Database');
```

### Output

```text
8
```

---

## Using Columns

```sql
SELECT LENGTH(employee_name)
FROM Employees;
```

---

## IV. CONCAT()

Combines multiple strings.

## Syntax

```sql
SELECT CONCAT(string1, string2);
```

---

## Example

```sql
SELECT CONCAT('Diya', ' ', 'Shah');
```

### Output

```text
Diya Shah
```

---

## Combining Columns

```sql
SELECT CONCAT(first_name, ' ', last_name)
FROM Employees;
```
## V. TRIM()
converts a string in proper manner by removing excess spces from start and end.
## Example

```sql
SELECT TRIM("       Diya Shah     ")
```

### Output
```text
Diya Shah
```

---
## VI. SUBSTRING()
Helps to extract a piece of text.

## Example
```sql
SELECT SUBSTRING('Database',1,4)
```
### Output
```text
Data
```

---
## VII. LEFT()
Helps to extract 'n' characters from left.
## Example
```sql
SELECT LEFT('Database',4)
```
### Output
```text
Data
```

---
## VIII. RIGHT()
Helps to extract 'n' characters from right.
## Example
```sql
SELECT RIGHT('Database',4)
```
### Output
```text
base
```
---

# 2. The "GLUE"
 
| CONCAT | Connects 2 or more strings together | ```sql SELECT CONCAT('Diya',' ','Shah') ``` | OUTPUT: ``` text Diya Shah ``` |
| ------ | ----------------------------------- | --------| ----------------------------------- |
---

# 3. The "LENGTH" & "LOCATION"
## I. LENGTH()
Tells us how many characters are there in the string.
## Example 
```sql
SELECT LENGTH('SQL')
```
### Output
```text
3
```
---
## II. REPLACE()
Swaps out one word with another.
## Example 
```sql
SELECT REPLACE('I LOVE SQL','PostgreSQL')
```
### Output
```text
I LOVE PostgreSQL
```
---

# 4. The "COUNTING" Machine

 
## Example
| user_id | email |
| ------- | ----- |
| 1 | alice@example.com|
| 2 | NULL |
| 3 | bob@example.com|
| 4 | NULL |
| 5 | alice@example.com|

| count(*) | count(1) | count(column_name) | count(DISTINCT column_name) |
| -------- | -------- | ------------------ | --------------------------- |
| Counts eveything including NULL values | Works similar to count(*) | Counts duplicates but ignores NULL values | count everything except NULL values or duplicates |
| 5 | 5 | 3 | 2 |

---
# 📖 FUNCTION SUMMARY

Imagine a library.
| AGGREGATION FUCTIONS                                       |
|-----------------------------------------------------------|

| SQL Function | Requirement        | Defination         | 
| ------------ | ------------------ | ------------ |
| COUNT()      | Count total books  | Counts the number of rows in the table |
| SUM()        | Calculate total cost of books | Adds up all the values in that particular column |
| AVG()        | Find average book price       | Finds out average of all the values present in that particular column |
| MIN()        | Find cheapest book            | Finds out the smallest value among all the values present in that particular column |
| MAX()        | Find most expensive book      | Finds out the largest value among all the values present in that particular column |

| STRING FUCTIONS                                       |
|-----------------------------------------------------------|

| SQL Function | Requirement        | Defination         | 
| ------------ | ------------------ | ------------ |
| UPPER()      | Rearranging books vertically | Convert entire string in a the cell to uppercase   |
| LOWER()      | Rearranging books horizontally | Convert entire string in a the cell to lowercase |
| TRIM()       | Fill in or remove the empty spaces within the books       |  Remove excess space                        | 
| SUBSTRING()  | Remove a particulr book according to user's demand       | Finds out string from a word for given range  |
| LEFT()       | Remove a particulr book according to user's demand from left direction            | Finds out string from a word for given range from the leftside |
| RIGHT()      | Remove a particulr book according to user's demand from right direction      | Finds out string from a word for given range from the rightside |
| LENGTH()     | Count total books  | Count characters present in a cell |
| CONCAT()     | Arrange similar books together  | Join strings                               |
| COUNT()      | Count total pages from a single book  | Counts the number of rows in the table |
| REPLACE()    | Exchange the book from one category with another one  | Exchange one string for another |

---

# 7️⃣ 📝 Practice Exercises

### Exercise 1

Count the total number of employees.

```sql
SELECT COUNT(*)
FROM Employees;
```

---

### Exercise 2

Calculate the total salary payout.

```sql
SELECT SUM(salary)
FROM Employees;
```

---

### Exercise 3

Find the average employee salary.

```sql
SELECT AVG(salary)
FROM Employees;
```

---

### Exercise 4

Find the minimum and maximum salary.

---

### Exercise 5

Convert employee names to uppercase.

---

### Exercise 6

Convert employee names to lowercase.

---

### Exercise 7

Find the length of employee names.

---

### Exercise 8

Combine first name and last name.

---


# 🎯 Key Takeaways

✅ Learned what SQL Functions are

✅ Understood Aggregate Functions

✅ Used COUNT(), SUM(), AVG(), MIN(), MAX()

✅ Learned String Functions

✅ Used UPPER(), LOWER(), TRIM(), SUBSTRING(), LEFT(), RIGHT(), LENGTH(), REPLACE(), CONCAT(), COUNT(*), COUNT(1), COUNT()

---

# 8️⃣ 📖 Day 8 Summary

Today, you learned how SQL Functions help perform calculations, summarize data, manipulate text efficiently. Functions are heavily used in reporting, analytics, dashboards, and real-world applications because they simplify complex operations into single commands.

Mastering SQL functions is a major step toward becoming proficient in database querying and data analysis.

---

## 9️⃣ 🚀 Coming Up Next: Day 9 – GROUP BY & HAVING Clause along with subsets

You'll learn:

```sql
GROUP BY
HAVING
```

and understand how to group records and perform powerful data analysis using aggregate functions.
---

# Progress Status: Day 8 Completed ✅
