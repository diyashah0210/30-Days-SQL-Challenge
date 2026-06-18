# 📘 30 Days Of SQL: Day 25 - Data Import & Export

Welcome to **Day 25** of the **30 Days of SQL** challenge! 🎉

In real-world projects, databases rarely start with empty tables. Data is constantly imported from files, applications, APIs, spreadsheets, and other databases. Similarly, organizations regularly export data for reporting, backups, analytics, migrations, and integrations.

Today, you'll learn how to efficiently **import, export, migrate, and back up data** using SQL tools and techniques.

---

# 📚 Table of Contents

1. Overview
2. What is Data Import & Export?
3. Why Import & Export is Important
4. Sources of Data
5. Data Import Methods
6. Importing CSV Files
7. LOAD DATA INFILE
8. BULK INSERT
9. Import Wizards
10. Importing JSON Data
11. Exporting Data
12. Exporting Query Results
13. Exporting to CSV
14. Database Backups
15. Database Restore
16. Data Migration
17. ETL Basics
18. Data Validation After Import
19. Common Import Errors
20. Best Practices
21. Real-World Use Cases
22. Hands-On Challenge
23. Practice Exercises
24. Key Takeaways
25. Day 25 Summary

---

# 🔍 Overview

Organizations constantly move data between systems.

Examples:

```text
Excel → SQL Database

Application → Database

Database → CSV File

Database → Data Warehouse
```

Data Import and Export allows databases to communicate with other systems efficiently.

---

# 📌 What is Data Import?

Data Import is the process of bringing external data into a database.

Examples:

- CSV Files
- Excel Sheets
- JSON Files
- APIs
- Other Databases

Example:

```text
customers.csv
        ↓
MySQL Database
```

---

# 📌 What is Data Export?

Data Export is the process of moving data from a database to another format.

Examples:

- CSV Reports
- Excel Reports
- JSON Files
- Backup Files

Example:

```text
MySQL Database
        ↓
sales_report.csv
```

---

# 🎯 Why Import & Export is Important

Benefits:

✅ Data Migration

✅ Reporting

✅ Analytics

✅ Data Warehousing

✅ Backup & Recovery

✅ System Integration

---

# 🌐 Sources of Data

Common sources include:

| Source | Example |
|----------|----------|
| CSV Files | customers.csv |
| Excel Files | sales.xlsx |
| JSON Files | api_data.json |
| APIs | Payment Gateway |
| Databases | MySQL → PostgreSQL |
| Applications | ERP Systems |

---

# 📥 Data Import Methods

There are several ways to import data:

1. Manual Entry
2. SQL Commands
3. Import Wizards
4. ETL Tools
5. APIs
6. Database Migration Tools

---

# 📄 Importing CSV Files

CSV (Comma Separated Values) is the most common import format.

Example CSV:

```csv
customer_id,name,city
1,John,Mumbai
2,Priya,Pune
3,Rahul,Delhi
```

Target Table:

```sql
CREATE TABLE Customers
(
    customer_id INT,
    name VARCHAR(100),
    city VARCHAR(100)
);
```

---

# ⚡ LOAD DATA INFILE (MySQL)

Fastest way to import large CSV files.

Syntax:

```sql
LOAD DATA INFILE 'customers.csv'
INTO TABLE Customers
FIELDS TERMINATED BY ','
LINES TERMINATED BY '\n'
IGNORE 1 ROWS;
```

Explanation:

- Reads file directly
- Skips header row
- Imports thousands of records quickly

---

# 🚀 BULK INSERT (SQL Server)

Used for importing large files.

Syntax:

```sql
BULK INSERT Customers
FROM 'C:\customers.csv'
WITH
(
    FIRSTROW = 2,
    FIELDTERMINATOR = ',',
    ROWTERMINATOR = '\n'
);
```

Advantages:

✅ Fast

✅ Efficient

✅ Enterprise-Scale Imports

---

# 🧙 Import Wizards

Most database tools provide graphical import utilities.

Examples:

- MySQL Workbench
- SQL Server Management Studio
- pgAdmin
- Oracle SQL Developer

Process:

```text
Select File
      ↓
Map Columns
      ↓
Validate Data
      ↓
Import
```

---

# 📦 Importing JSON Data

Modern applications frequently exchange JSON data.

Example JSON:

```json
{
  "customer_id": 1,
  "name": "John",
  "city": "Mumbai"
}
```

MySQL Example:

```sql
SELECT JSON_EXTRACT(
    '{"name":"John"}',
    '$.name'
);
```

---

# 📤 Exporting Data

Exporting allows data sharing and reporting.

Common export formats:

- CSV
- Excel
- JSON
- XML
- SQL Backup Files

---

# 📊 Exporting Query Results

Example:

```sql
SELECT *
FROM Orders
WHERE order_date >= '2025-01-01';
```

Results can be exported into:

```text
CSV
Excel
PDF Reports
```

---

# 📄 Exporting to CSV

MySQL Example:

```sql
SELECT *
INTO OUTFILE 'orders.csv'
FIELDS TERMINATED BY ','
LINES TERMINATED BY '\n'
FROM Orders;
```

---

# 💾 Database Backups

Backups protect against:

❌ Data Loss

❌ Hardware Failure

❌ Human Errors

❌ Cyber Attacks

---

# 🛡 Backup Types

## Full Backup

Entire database.

```text
Database
↓
Complete Backup
```

---

## Incremental Backup

Only changed data.

```text
Previous Backup
↓
New Changes Only
```

---

## Differential Backup

Changes since last full backup.

---

# 💻 MySQL Backup

Using mysqldump:

```bash
mysqldump -u root -p company_db > company_backup.sql
```

---

# 🔄 Database Restore

Restore backup:

```bash
mysql -u root -p company_db < company_backup.sql
```

---

# 🔀 Data Migration

Migration means moving data between systems.

Examples:

```text
MySQL
   ↓
PostgreSQL
```

```text
Legacy System
   ↓
Modern ERP
```

Migration involves:

- Schema Transfer
- Data Transfer
- Validation
- Testing

---

# 🔄 ETL Basics

ETL stands for:

## Extract

Collect data.

```text
CRM
ERP
CSV
```

---

## Transform

Clean and modify data.

Example:

```text
john smith
↓
John Smith
```

---

## Load

Store into destination database.

```text
Data Warehouse
```

---

# ✅ Data Validation After Import

Always validate imported data.

Example:

Count records:

```sql
SELECT COUNT(*)
FROM Customers;
```

Check NULL values:

```sql
SELECT *
FROM Customers
WHERE name IS NULL;
```

Check duplicates:

```sql
SELECT customer_id,
COUNT(*)
FROM Customers
GROUP BY customer_id
HAVING COUNT(*) > 1;
```

---

# ⚠ Common Import Errors

## Incorrect Data Types

Example:

```text
ABC
```

Inserted into:

```sql
INT
```

---

## Missing Columns

CSV structure doesn't match table structure.

---

## Duplicate Primary Keys

Violates uniqueness constraints.

---

## Incorrect Date Formats

Example:

```text
31/12/2025
```

Expected:

```text
2025-12-31
```

---

# 🔧 Best Practices

✅ Always backup before importing

✅ Validate source data

✅ Use staging tables

✅ Check duplicates

✅ Verify imported row counts

✅ Test imports in development environments

✅ Automate repetitive imports

---

# 🏢 Real-World Use Cases

## Banking

Import transaction files daily.

---

## E-Commerce

Import product catalogs.

---

## HR Systems

Import employee records.

---

## Healthcare

Import patient data from clinics.

---

## Analytics

Load data into data warehouses.

---

# 🎨 Hands-On Challenge

1. Create a Customers table.
2. Import customer records from CSV.
3. Validate imported data.
4. Export customer reports.
5. Create a database backup.
6. Restore the backup successfully.

---

# 💻 Practice Exercises

## ✅ Level 1

1. Create a table for importing CSV data.
2. Import a customer CSV file.
3. Export a table into CSV format.
4. Count imported records.
5. Check for duplicate records.

---

## 🚀 Level 2

1. Design a complete ETL workflow.
2. Import JSON customer data.
3. Create automated backup scripts.
4. Validate migrated data.
5. Design a data migration strategy.

---

# 🎯 Key Takeaways

✅ Data Import loads external data into databases.

✅ Data Export shares database information externally.

✅ CSV is the most common import/export format.

✅ LOAD DATA INFILE and BULK INSERT provide high-speed imports.

✅ Backups protect against data loss.

✅ ETL is the foundation of data engineering.

✅ Data validation is critical after imports.

✅ Import & Export skills are essential in real-world SQL projects.

---

# 📝 Day 25 Summary

Today, you learned how databases exchange information with external systems through Data Import and Export techniques. You explored CSV imports, LOAD DATA INFILE, BULK INSERT, JSON data handling, exports, backups, restoration processes, migration strategies, ETL concepts, and validation techniques.

These skills are essential for database administrators, data engineers, analysts, and software developers working with real-world data systems.

---

## 🚀 Coming Up Next: Day 26 – SQL for Analytics

### Topics Covered

- KPI Analysis
- Revenue Analysis
- Profit Analysis
- Customer Analytics
- Sales Analytics
- Product Analytics
- Trend Analysis
- Dashboard Queries
- Business Reporting
- Real-World Analytics

## Progress Status: Day 25 Completed ✅
[PREVIOUS: DAY24-TRIGGERS AND EVENTS](https://github.com/diyashah0210/30-Days-SQL-Challenge/tree/3e62eb1375dcd1799bd61623da65863ba824f7c2/DAY24)👆\
[NEXT: DAY26-SQL FOR ANALYTICS](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/3e62eb1375dcd1799bd61623da65863ba824f7c2/DAY26/DAY26-%20SQL%20for%20Analytics.md)👇
