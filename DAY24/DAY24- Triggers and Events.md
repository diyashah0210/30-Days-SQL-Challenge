# 📘 30 Days Of SQL: Day 24 - Triggers & Events

Welcome to **Day 24** of the **30 Days of SQL** challenge! 🎉

So far, we have learned how to design databases, store data, retrieve information, optimize queries, and maintain data integrity. Today, we'll learn how databases can **automatically react to changes** and **schedule tasks without human intervention** using **Triggers** and **Events**.

These features are widely used in:

- Banking Systems
- Inventory Management
- Audit Logging
- Payroll Systems
- E-Commerce Applications
- Data Warehousing

---

# 📚 Table of Contents

- [🔍 Overview](#-overview)
- [📌 What are Triggers?](#-what-are-triggers)
- [🎯 Why Triggers are Important](#-why-triggers-are-important)
- [⚙ How Triggers Work](#-how-triggers-work)
- [📖 Trigger Execution Flow](#-trigger-execution-flow)
- [🔄 Types of Triggers](#-types-of-triggers)
- [1️⃣ BEFORE INSERT Trigger](#1️⃣-before-insert-trigger)
- [2️⃣ AFTER INSERT Trigger](#2️⃣-after-insert-trigger)
- [3️⃣ BEFORE UPDATE Trigger](#3️⃣-before-update-trigger)
- [4️⃣ AFTER UPDATE Trigger](#4️⃣-after-update-trigger)
- [5️⃣ BEFORE DELETE Trigger](#5️⃣-before-delete-trigger)
- [6️⃣ AFTER DELETE Trigger](#6️⃣-after-delete-trigger)
- [📊 OLD vs NEW Keywords](#-old-vs-new-keywords)
- [🔁 Row-Level vs Statement-Level Triggers](#-row-level-vs-statement-level-triggers)
- [🏢 Real-World Trigger Examples](#-real-world-trigger-examples)
- [⏰ What are Events?](#-what-are-events)
- [🎯 Why Events are Important](#-why-events-are-important)
- [📅 Event Scheduler](#-event-scheduler)
- [🕒 One-Time Events](#-one-time-events)
- [🔄 Recurring Events](#-recurring-events)
- [🏢 Real-World Event Examples](#-real-world-event-examples)
- [⚠ Common Mistakes](#-common-mistakes)
- [🎨 Hands-On Challenge](#-hands-on-challenge)
- [💻 Exercises](#-exercises)
- [🎯 Key Takeaways](#-key-takeaways)
- [📝 Day 24 Summary](#-day-24-summary)

---

# 🔍 Overview

Triggers and Events help automate database operations.

Instead of manually executing repetitive tasks, the database can automatically:

✅ Validate Data

✅ Maintain Audit Logs

✅ Track Changes

✅ Generate Reports

✅ Clean Old Data

✅ Schedule Maintenance Activities

---

# 📌 What are Triggers?

A **Trigger** is a special database object that automatically executes when a specific event occurs on a table.

Think of a trigger as:

```text
IF Something Happens
THEN Automatically Execute SQL Code
```

Triggers respond to:

- INSERT
- UPDATE
- DELETE

operations.

---

# 🎯 Why Triggers are Important

Without Triggers:

```text
Insert Employee
↓
Manually Create Audit Record
```

With Triggers:

```text
Insert Employee
↓
Audit Record Created Automatically
```

Benefits:

✅ Automation

✅ Data Validation

✅ Audit Logging

✅ Business Rule Enforcement

✅ Data Consistency

---

# ⚙ How Triggers Work

A trigger listens for a database event.

```text
INSERT
UPDATE
DELETE
```

When the event occurs:

```text
Event Occurs
     ↓
Trigger Fires
     ↓
SQL Logic Executes
```

---

# 📖 Trigger Execution Flow

```text
User Executes INSERT
         ↓
BEFORE INSERT Trigger
         ↓
Data Inserted
         ↓
AFTER INSERT Trigger
```

---

# 🔄 Types of Triggers

| Trigger Type | Executes |
|-------------|-----------|
| BEFORE INSERT | Before data insertion |
| AFTER INSERT | After insertion |
| BEFORE UPDATE | Before update |
| AFTER UPDATE | After update |
| BEFORE DELETE | Before deletion |
| AFTER DELETE | After deletion |

---

# 1️⃣ BEFORE INSERT Trigger

Runs before data is inserted.

### Example

```sql
CREATE TRIGGER trg_before_employee_insert
BEFORE INSERT
ON Employees
FOR EACH ROW
SET NEW.created_date = NOW();
```

### Use Cases

- Auto-fill values
- Data validation
- Default values

---

# 2️⃣ AFTER INSERT Trigger

Runs after insertion.

### Example

```sql
CREATE TRIGGER trg_after_employee_insert
AFTER INSERT
ON Employees
FOR EACH ROW
INSERT INTO Employee_Audit
(
    employee_id,
    action_performed,
    action_date
)
VALUES
(
    NEW.employee_id,
    'INSERT',
    NOW()
);
```

### Use Cases

- Audit Logs
- Notifications
- Activity Tracking

---

# 3️⃣ BEFORE UPDATE Trigger

Runs before updating data.

### Example

```sql
CREATE TRIGGER trg_before_salary_update
BEFORE UPDATE
ON Employees
FOR EACH ROW
BEGIN

IF NEW.salary < 0 THEN

SIGNAL SQLSTATE '45000'
SET MESSAGE_TEXT = 'Salary cannot be negative';

END IF;

END;
```

### Use Cases

- Validation
- Prevent Invalid Updates

---

# 4️⃣ AFTER UPDATE Trigger

Runs after updates.

### Example

```sql
CREATE TRIGGER trg_after_salary_update
AFTER UPDATE
ON Employees
FOR EACH ROW

INSERT INTO Salary_History
(
    employee_id,
    old_salary,
    new_salary
)
VALUES
(
    OLD.employee_id,
    OLD.salary,
    NEW.salary
);
```

### Use Cases

- Track Changes
- Historical Records

---

# 5️⃣ BEFORE DELETE Trigger

Runs before deletion.

### Example

```sql
CREATE TRIGGER trg_before_delete
BEFORE DELETE
ON Employees
FOR EACH ROW

INSERT INTO Deleted_Employees
VALUES
(
    OLD.employee_id,
    OLD.employee_name
);
```

### Use Cases

- Data Backup
- Archiving

---

# 6️⃣ AFTER DELETE Trigger

Runs after deletion.

### Example

```sql
CREATE TRIGGER trg_after_delete
AFTER DELETE
ON Employees
FOR EACH ROW

INSERT INTO Audit_Log
VALUES
(
    OLD.employee_id,
    'DELETE',
    NOW()
);
```

### Use Cases

- Deletion Tracking
- Security Auditing

---

# 📊 OLD vs NEW Keywords

Triggers often use OLD and NEW values.

| Keyword | Meaning |
|----------|----------|
| OLD | Value before change |
| NEW | Value after change |

### Example

```sql
OLD.salary
```

Salary before update.

```sql
NEW.salary
```

Salary after update.

---

# 🔁 Row-Level vs Statement-Level Triggers

## Row-Level Trigger

Executes once for each affected row.

Example:

```text
100 Rows Updated
↓
Trigger Executes 100 Times
```

---

## Statement-Level Trigger

Executes once per SQL statement.

Example:

```text
100 Rows Updated
↓
Trigger Executes Once
```

---

# 🏢 Real-World Trigger Examples

## Banking

Track balance changes.

---

## HR Systems

Maintain salary history.

---

## Inventory

Reduce stock when orders are placed.

---

## Healthcare

Log patient record updates.

---

## E-Commerce

Track order status changes.

---

# ⏰ What are Events?

An **Event** is a scheduled task executed automatically by the database.

Think of it as:

```text
Database Alarm Clock
```

---

# 🎯 Why Events are Important

Events automate repetitive tasks.

Benefits:

✅ Scheduled Reports

✅ Database Cleanup

✅ Monthly Backups

✅ Archiving Records

✅ Maintenance Tasks

---

# 📅 Event Scheduler

The Event Scheduler controls whether events can run.

Enable it:

```sql
SET GLOBAL event_scheduler = ON;
```

Verify:

```sql
SHOW VARIABLES LIKE 'event_scheduler';
```

---

# 🕒 One-Time Events

Execute once at a specified date and time.

### Example

```sql
CREATE EVENT cleanup_event

ON SCHEDULE
AT '2026-01-01 00:00:00'

DO

DELETE FROM Temp_Data;
```

---

# 🔄 Recurring Events

Execute repeatedly.

### Daily Cleanup

```sql
CREATE EVENT daily_cleanup

ON SCHEDULE
EVERY 1 DAY

DO

DELETE FROM Temp_Data;
```

---

### Weekly Report

```sql
CREATE EVENT weekly_report

ON SCHEDULE
EVERY 1 WEEK

DO

CALL Generate_Report();
```

---

### Monthly Archive

```sql
CREATE EVENT monthly_archive

ON SCHEDULE
EVERY 1 MONTH

DO

INSERT INTO Archived_Orders
SELECT *
FROM Orders
WHERE order_date < CURDATE() - INTERVAL 1 YEAR;
```

---

# 🏢 Real-World Event Examples

## Banking

Daily interest calculations.

---

## HR Systems

Monthly payroll processing.

---

## E-Commerce

Weekly sales reports.

---

## Healthcare

Monthly record archiving.

---

## Logistics

Shipment status updates.

---

# ⚠ Common Mistakes

### ❌ Infinite Trigger Loops

Trigger updates same table repeatedly.

---

### ❌ Complex Trigger Logic

Makes transactions slower.

---

### ❌ Forgetting Event Scheduler

Events never execute.

---

### ❌ Missing Audit Tables

Trigger execution fails.

---

### ❌ Excessive Event Frequency

Can overload servers.

---

# 🎨 Hands-On Challenge

1. Create a BEFORE INSERT trigger validating employee age.
2. Create an AFTER INSERT trigger storing audit records.
3. Create an AFTER UPDATE trigger storing salary history.
4. Create an AFTER DELETE trigger logging deletions.
5. Create a recurring event generating weekly reports.
6. Create a monthly archive event.

---

# 💻 Exercises

## ✅ Level 1

1. Create a BEFORE INSERT trigger.
2. Create an AFTER INSERT trigger.
3. Create an AFTER UPDATE trigger.
4. Enable Event Scheduler.
5. Create a one-time cleanup event.

---

## 🚀 Level 2

1. Build an employee audit system using triggers.
2. Create a salary tracking system.
3. Design a stock management trigger.
4. Create a monthly archive event.
5. Build a complete automated reporting solution.

---

# 🎯 Key Takeaways

✅ Triggers execute automatically when data changes.

✅ Triggers can respond to INSERT, UPDATE, and DELETE operations.

✅ BEFORE triggers execute before data changes.

✅ AFTER triggers execute after data changes.

✅ OLD and NEW help access record values.

✅ Events execute automatically on a schedule.

✅ Event Scheduler must be enabled.

✅ Events automate repetitive administrative tasks.

✅ Triggers and Events improve automation and consistency.

---

# 📝 Day 24 Summary

Today, you learned how databases can automate actions using Triggers and Events.

You explored different trigger types, trigger execution flow, OLD and NEW values, audit logging techniques, event scheduling, recurring tasks, and real-world automation scenarios.

These concepts are heavily used in enterprise systems to reduce manual work, enforce business rules, and maintain data integrity.

---

## 🚀 Coming Up Next: Day 25 – Data Import & Export

### Topics Covered

- Importing CSV Files
- Exporting Data
- LOAD DATA INFILE
- BULK INSERT
- Import Wizards
- Database Backups
- Data Migration
- ETL Concepts

## Progress Status: Day 24 Completed ✅
[PREVIOUS: DAY23-DATA MODELING & NORMALIZATION](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/df4b0211c1cd4f7c7ac2f59702c3f939195cca81/DAY23/DAY23-%20Data%20Modeling%20%26%20Normalization.md)👆\
[NEXT: DAY25-DATA IMPORT AND EXPORT]()👇
