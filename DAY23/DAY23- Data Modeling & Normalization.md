# 📘 30 Days Of SQL: Day 23 - Data Modeling & Normalization

Welcome to **Day 23** of the **30 Days of SQL** challenge! 🎉

Before creating tables and writing queries, every database must be properly designed. A well-designed database reduces redundancy, improves performance, maintains data integrity, and scales efficiently as data grows.

Today, we'll explore **Data Modeling** and **Normalization**, two fundamental concepts used by database architects and developers to build robust database systems.

---

# 📚 Table of Contents

- [🔍 Overview](#-overview)
- [📈 What is Data Modeling?](#-what-is-data-modeling)
- [🎯 Why Data Modeling is Important](#-why-data-modeling-is-important)
- [🏗 Types of Data Models](#-types-of-data-models)
  - [1. Conceptual Model](#1-conceptual-model)
  - [2. Logical Model](#2-logical-model)
  - [3. Physical Model](#3-physical-model)
- [🧩 Understanding Entities](#-understanding-entities)
- [🏷 Understanding Attributes](#-understanding-attributes)
- [🔗 Understanding Relationships](#-understanding-relationships)
- [🔄 What is Normalization?](#-what-is-normalization)
- [🎯 Why Normalization is Important](#-why-normalization-is-important)
- [⚠ Data Redundancy & Anomalies](#-data-redundancy--anomalies)
- [1️⃣ First Normal Form (1NF)](#1️⃣-first-normal-form-1nf)
- [2️⃣ Second Normal Form (2NF)](#2️⃣-second-normal-form-2nf)
- [3️⃣ Third Normal Form (3NF)](#3️⃣-third-normal-form-3nf)
- [4️⃣ Boyce-Codd Normal Form (BCNF)](#4️⃣-boyce-codd-normal-form-bcnf)
- [🔄 Denormalization](#-denormalization)
- [🏢 Real-World Database Design Example](#-real-world-database-design-example)
- [🔧 Best Practices](#-best-practices)
- [❌ Common Design Mistakes](#-common-design-mistakes)
- [🎨 Hands-On Challenge](#-hands-on-challenge)
- [💻 Exercises](#-exercises)
- [🎯 Key Takeaways](#-key-takeaways)
- [📝 Day 23 Summary](#-day-23-summary)

---

# 🔍 Overview

Data modeling is the process of designing how information is stored, connected, and managed inside a database.

Before writing SQL queries, database architects determine:

- What data needs to be stored
- How tables should relate
- How duplication can be minimized
- How future growth will be supported

A well-designed database improves:

✅ Data Integrity

✅ Query Performance

✅ Scalability

✅ Maintainability

---

# 📈 What is Data Modeling?

Data Modeling is the process of creating a blueprint for a database.

Just like an architect creates a building plan before construction, database designers create a model before creating tables.

The model defines:

- Entities
- Attributes
- Relationships
- Business Rules

---

# 🎯 Why Data Modeling is Important

Poor database design can lead to:

❌ Duplicate Data

❌ Slow Queries

❌ Inconsistent Records

❌ Difficult Maintenance

Good database design provides:

✅ Reduced Redundancy

✅ Better Data Integrity

✅ Easier Querying

✅ Improved Performance

---

# 🏗 Types of Data Models

## 1. Conceptual Model

High-level business representation.

Example:

```text
Customer → Places → Order
```

Focuses on:

- Business Requirements
- Entities
- Relationships

---

## 2. Logical Model

Adds:

- Attributes
- Keys
- Constraints

Example:

```text
Customers
-----------
Customer_ID
Name
Email

Orders
-----------
Order_ID
Order_Date
Customer_ID
```

---

## 3. Physical Model

Actual SQL implementation.

Example:

```sql
CREATE TABLE Customers
(
    Customer_ID INT PRIMARY KEY,
    Name VARCHAR(100),
    Email VARCHAR(100)
);
```
<img width="591" height="232" alt="image" src="https://github.com/user-attachments/assets/01141682-4aa6-42ba-b86c-5ec64482e170" />

---

# 🧩 Understanding Entities

An Entity represents a real-world object.

Examples:

| Domain | Entity |
|----------|----------|
| Banking | Customer |
| School | Student |
| Hospital | Patient |
| HR | Employee |
| E-Commerce | Product |

---

# 🏷 Understanding Attributes

Attributes describe an entity.

Example:

Employee

- Employee_ID
- Employee_Name
- Salary
- Department

## Types of Attributes

### Simple Attribute

Cannot be divided further.

Examples:

- Gender
- Salary

### Composite Attribute

Can be broken into smaller parts.

Example:

Address

- Street
- City
- State
- Country

### Derived Attribute

Calculated from another attribute.

Example:

Age derived from Date_of_Birth

### Multi-Valued Attribute

Can contain multiple values.

Example:

Phone Numbers

---

# 🔗 Understanding Relationships

Relationships connect entities together.

Examples:

```text
Customer → Order

Doctor → Patient

Student → Course
```

These relationships help databases represent real-world interactions.

---

# 🔄 What is Normalization?

Normalization is the process of organizing data to reduce redundancy and improve consistency.

Goal:

```text
Store Once
Use Many Times
```

---

# 🎯 Why Normalization is Important

Without normalization:

| Customer | Phone |
|-----------|---------|
| Alice | 9999999999 |
| Alice | 9999999999 |
| Alice | 9999999999 |

The same information is repeated multiple times.

This causes:

❌ Data Redundancy

❌ Storage Waste

❌ Update Problems

---

# ⚠ Data Redundancy & Anomalies

## Insert Anomaly

Cannot insert information because some related data is missing.

### Example

You cannot add a new course until a student enrolls in it.

---

## Update Anomaly

Updating one record requires updating multiple rows.

### Example

Changing a customer's phone number requires updating hundreds of records.

---

## Delete Anomaly

Deleting a record accidentally removes important information.

### Example

Deleting the last enrolled student may remove course information.

---
<img width="371" height="188" alt="image" src="https://github.com/user-attachments/assets/708e419b-4f66-4501-ac6e-d70bdc439221" />

# 1️⃣ First Normal Form (1NF)

## Rules

✅ Atomic Values

✅ No Repeating Groups

### Before 1NF

| Student | Subjects |
|----------|----------|
| John | Math, Science |

### After 1NF

| Student | Subject |
|----------|----------|
| John | Math |
| John | Science |

---

# 2️⃣ Second Normal Form (2NF)

## Requirements

✅ Must satisfy 1NF

✅ Remove Partial Dependencies

### Before 2NF

| Student_ID | Course_ID | Student_Name |
|------------|------------|--------------|

Student_Name depends only on Student_ID.

### After 2NF

#### Students

| Student_ID | Student_Name |
|------------|--------------|

#### Enrollments

| Student_ID | Course_ID |
|------------|------------|

---

# 3️⃣ Third Normal Form (3NF)

## Requirements

✅ Must satisfy 2NF

✅ Remove Transitive Dependencies

### Before 3NF

| Employee_ID | Department_ID | Department_Name |
|------------|---------------|-----------------|

### After 3NF

#### Employees

| Employee_ID | Department_ID |

#### Departments

| Department_ID | Department_Name |

---

# 4️⃣ Boyce-Codd Normal Form (BCNF)

BCNF is a stricter version of 3NF.

### Rule

Every determinant must be a candidate key.

BCNF eliminates complex dependency issues that may still exist in 3NF.

---

# 🔄 Denormalization

Denormalization is the process of intentionally adding redundancy to improve performance.

Example:

Instead of joining:

```text
Customers
Orders
```

Store:

```text
Customer_Name
```

inside the Orders table.

## Benefits

✅ Faster Queries

✅ Faster Reports

## Drawbacks

❌ Duplicate Data

❌ Increased Maintenance

---

# 🏢 Real-World Database Design Example

## E-Commerce System

### Customers

```text
Customer_ID
Name
Email
Phone
```

### Products

```text
Product_ID
Product_Name
Price
```

### Orders

```text
Order_ID
Customer_ID
Order_Date
```

### Order_Items

```text
Order_ID
Product_ID
Quantity
```

### Relationships

```text
Customer → Orders

Orders → Order_Items

Products → Order_Items
```

---

# 🔧 Best Practices

✅ Use meaningful table names

✅ Define primary keys

✅ Use foreign keys

✅ Normalize up to 3NF whenever possible

✅ Avoid storing duplicate information

✅ Document database designs

---

# ❌ Common Design Mistakes

- Missing Primary Keys
- Storing Multiple Values in One Column
- Excessive Redundancy
- Ignoring Foreign Keys
- Over-Denormalization
- Poor Naming Conventions

---

## 🎨 Hands-On Challenge

1. Design a database for a Library System.
2. Normalize an unstructured Orders table to 3NF.
3. Identify entities and attributes for a Hospital Database.
4. Create a logical data model for an E-Commerce Platform.
5. Compare Normalization vs Denormalization for reporting systems.
## 💻 Exercises

1. Convert a table into 1NF.
2. Identify partial dependencies.
3. Identify transitive dependencies.
4. Design entities for a Banking System.
5. List attributes for a Student entity.
1. Normalize a Customer Orders table into 3NF.
2. Design a normalized HR database.
3. Create SQL tables from a logical model.
4. Identify candidate keys.
5. Determine when denormalization is beneficial.

---

# 🎯 Key Takeaways

✅ Data Modeling creates the blueprint for a database.

✅ Entities represent real-world objects.

✅ Attributes describe entities.

✅ Relationships connect entities.

✅ Normalization reduces redundancy.

✅ 1NF removes repeating groups.

✅ 2NF removes partial dependencies.

✅ 3NF removes transitive dependencies.

✅ BCNF strengthens normalization.

✅ Denormalization improves performance when used carefully.

---

# 📝 Day 23 Summary

Today, you learned how professional databases are designed before implementation. You explored Data Modeling concepts, understood how entities, attributes, and relationships are structured, and learned how Normalization helps create efficient, scalable, and maintainable databases.

These concepts form the foundation of every enterprise database system and are essential for database developers, data analysts, and software engineers.

---

## 🚀 Coming Up Next: Day 24 – Triggers & Events

### Topics Covered

- BEFORE & AFTER Triggers
- INSERT, UPDATE & DELETE Triggers
- Audit Logging
- Business Rule Enforcement
- Event Scheduler
- One-Time Events
- Recurring Events
- Database Automation

## Progress Status: Day 23 Completed ✅
---

[PREVIOUS: DAY22-SQL MASTERY ASSESSMENT-3](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/e389fcbdf19ed36741f2581bf383277be5fa6e6b/DAY22/DAY22-%20SQL%20Mastery%20Assessment-3.md)👆\
[NEXT: DAY24-TRIGGERS & EVENTS]()👇
