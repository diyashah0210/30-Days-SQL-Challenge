# 📘 30 Days Of SQL: Day 28 - SQL Security & User Management

Welcome to **Day 28** of the **30 Days of SQL** challenge! 🎉

Databases often store an organization's most valuable asset: **data**. Customer information, employee records, financial transactions, medical records, and business intelligence all reside within databases.

As databases become larger and more accessible, security becomes increasingly important. A single security vulnerability can result in data breaches, financial losses, legal issues, and reputational damage.

Today, you'll learn how to secure databases using **authentication**, **authorization**, **roles**, **permissions**, **encryption**, and **security best practices**.

---

# 📚 Table of Contents

1. Overview
2. Why Database Security Matters
3. Security Threats
4. Authentication vs Authorization
5. Database Users
6. Roles and Permissions
7. GRANT Statement
8. REVOKE Statement
9. Principle of Least Privilege
10. Data Access Control
11. SQL Injection
12. Preventing SQL Injection
13. Row-Level Security
14. Column-Level Security
15. Data Masking
16. Encryption Basics
17. Password Security
18. Auditing and Monitoring
19. Backup Security
20. Real-World Security Examples
21. Common Security Mistakes
22. Best Practices
23. Hands-On Challenge
24. Practice Exercises
25. Key Takeaways
26. Day 28 Summary

---

# 🔍 Overview

Database Security is the practice of protecting databases from:

❌ Unauthorized Access

❌ Data Theft

❌ Data Corruption

❌ Accidental Changes

❌ Malicious Attacks

A secure database ensures:

✅ Confidentiality

✅ Integrity

✅ Availability

These three principles form the foundation of database security.

---

# 🎯 Why Database Security Matters

Imagine the following scenarios:

### Banking System

Unauthorized access to customer accounts.

---

### Hospital

Patient medical records exposed.

---

### E-Commerce

Credit card information stolen.

---

### HR Department

Employee salary information leaked.

---

Consequences:

❌ Financial Loss

❌ Legal Penalties

❌ Customer Distrust

❌ Operational Disruption

---

# ⚠ Security Threats

Common database threats include:

| Threat | Description |
|----------|-------------|
| SQL Injection | Malicious SQL execution |
| Unauthorized Access | Illegal data access |
| Weak Passwords | Easy account compromise |
| Insider Threats | Misuse by authorized users |
| Data Leakage | Exposure of sensitive information |
| Malware | Database corruption or theft |

---

# 🔐 Authentication vs Authorization

These terms are often confused.

---

## Authentication

Authentication answers:

```text
Who are you?
```

Examples:

- Username
- Password
- Multi-Factor Authentication

---

## Authorization

Authorization answers:

```text
What are you allowed to do?
```

Examples:

- Read Data
- Insert Data
- Delete Data
- Manage Users

---

# 👤 Database Users

A user account allows access to the database.

Example:

```sql
CREATE USER 'john'
IDENTIFIED BY 'SecurePassword123';
```

Purpose:

- Identify users
- Track activity
- Manage permissions

---

# 👥 Roles and Permissions

Instead of assigning permissions individually, permissions are grouped into roles.

Example:

| Role | Permissions |
|--------|-------------|
| Admin | Full Access |
| Manager | Read & Update |
| Analyst | Read Only |
| Auditor | Reporting Access |

Benefits:

✅ Easier Management

✅ Better Security

✅ Scalability

---

# 🛡 GRANT Statement

Used to provide permissions.

Syntax:

```sql
GRANT permission
ON table_name
TO user_name;
```

Example:

```sql
GRANT SELECT
ON Employees
TO analyst_user;
```

Now the user can read employee data.

---

# 🛡 Multiple Permissions

```sql
GRANT
SELECT,
INSERT,
UPDATE
ON Employees
TO hr_manager;
```

---

# 🚫 REVOKE Statement

Used to remove permissions.

Syntax:

```sql
REVOKE permission
ON table_name
FROM user_name;
```

Example:

```sql
REVOKE DELETE
ON Employees
FROM analyst_user;
```

---

# 🎯 Principle of Least Privilege

One of the most important security principles.

Rule:

```text
Give users only the permissions they need.
```

Example:

### Wrong

```text
Intern → Full Database Access
```

---

### Correct

```text
Intern → Read-Only Access
```

Benefits:

✅ Reduced Risk

✅ Better Control

✅ Improved Security

---

# 🔒 Data Access Control

Access can be restricted at different levels.

### Database Level

Access entire database.

---

### Table Level

Access specific tables.

---

### Row Level

Access specific records.

---

### Column Level

Access specific columns.

---

# 💉 SQL Injection

One of the most dangerous database attacks.

Example Application Query:

```sql
SELECT *
FROM Users
WHERE username = 'user'
AND password = 'password';
```

Attacker Input:

```text
' OR 1=1 --
```

Result:

```sql
SELECT *
FROM Users
WHERE username=''
OR 1=1;
```

The attacker may gain access.

---

# 🛡 Preventing SQL Injection

## Use Parameterized Queries

Example:

```sql
SELECT *
FROM Users
WHERE username = ?
AND password = ?;
```

---

## Validate Input

Accept only expected values.

---

## Limit User Permissions

Even if attacked, damage remains limited.

---

## Never Concatenate SQL Strings

Avoid:

```text
"SELECT * FROM Users WHERE ID=" + user_input
```

---

# 📍 Row-Level Security

Restricts which rows users can see.

Example:

Sales Managers should only view data from their region.

```text
North Manager → North Data

South Manager → South Data
```

Benefits:

✅ Better Privacy

✅ Better Compliance

---

# 📊 Column-Level Security

Restricts access to specific columns.

Example:

| Column | Access |
|----------|---------|
| Employee_Name | Yes |
| Salary | No |
| SSN | No |

Used extensively in HR and Banking systems.

---

# 🎭 Data Masking

Sensitive data is partially hidden.

Example:

```text
9876543210
```

Displayed as:

```text
98******10
```

Examples:

- Phone Numbers
- Credit Cards
- Government IDs

---

# 🔐 Encryption Basics

Encryption converts readable data into unreadable format.

---

## Data at Rest

Stored inside database.

```text
Database Files
```

Encrypted using:

- AES
- TDE (Transparent Data Encryption)

---

## Data in Transit

Data moving across networks.

Protected using:

```text
SSL/TLS
```

---

# 🔑 Password Security

Never store passwords as plain text.

❌ Bad

```text
password123
```

---

✅ Good

Store:

```text
Hashed Password
```

Algorithms:

- SHA-256
- bcrypt
- Argon2

---

# 📋 Auditing and Monitoring

Track database activity.

Monitor:

- Login Attempts
- Failed Logins
- Permission Changes
- Data Modifications

Benefits:

✅ Security Monitoring

✅ Compliance

✅ Forensics

---

# 💾 Backup Security

Backups often contain sensitive information.

Always:

✅ Encrypt Backups

✅ Restrict Access

✅ Store Securely

✅ Test Recovery Procedures

---

# 🏢 Real-World Security Examples

## Banking

- Encrypted Transactions
- Multi-Factor Authentication
- Audit Logs

---

## Healthcare

- HIPAA Compliance
- Patient Data Protection
- Role-Based Access

---

## E-Commerce

- Customer Data Security
- Payment Information Protection
- Fraud Monitoring

---

## Government

- Classified Information Protection
- Access Controls
- Security Auditing

---

# ❌ Common Security Mistakes

### Using Shared Accounts

No accountability.

---

### Weak Passwords

Easy compromise.

---

### Excessive Permissions

Increases risk.

---

### Ignoring SQL Injection

Major security vulnerability.

---

### Unencrypted Backups

Data exposure risk.

---

### No Auditing

Difficult to detect attacks.

---

# 🔧 Best Practices

✅ Use Strong Passwords

✅ Enable Multi-Factor Authentication

✅ Follow Least Privilege Principle

✅ Use Roles Instead of Direct Permissions

✅ Encrypt Sensitive Data

✅ Audit User Activity

✅ Secure Backups

✅ Regularly Review Permissions

✅ Prevent SQL Injection

✅ Keep Database Software Updated

---

# 🎨 Hands-On Challenge

1. Create database users with different roles.
2. Grant SELECT permission to an analyst.
3. Revoke DELETE permission from a user.
4. Design a row-level security scenario.
5. Create a security plan for an e-commerce database.
6. Identify SQL Injection vulnerabilities in sample queries.

---

# 💻 Practice Exercises

## ✅ Level 1

1. Create a database user.
2. Grant SELECT permission on a table.
3. Revoke INSERT permission.
4. Identify authentication and authorization examples.
5. Explain SQL Injection.

---

## 🚀 Level 2

1. Design role-based access control for a company.
2. Create a permission matrix for HR, Finance, and IT departments.
3. Build a security policy using least privilege principles.
4. Design an audit logging strategy.
5. Create a complete database security architecture for an online banking system.

---

# 🎯 Key Takeaways

✅ Database security protects data confidentiality, integrity, and availability.

✅ Authentication verifies identity.

✅ Authorization determines permissions.

✅ Users and roles simplify permission management.

✅ GRANT and REVOKE control access.

✅ SQL Injection is one of the most dangerous database attacks.

✅ Encryption protects sensitive data.

✅ Auditing helps detect and investigate security incidents.

✅ The Principle of Least Privilege is fundamental to database security.

---

# 📝 Day 28 Summary

Today, you learned how modern database systems protect sensitive information through authentication, authorization, access control, encryption, auditing, and security best practices. You explored user management, roles, permissions, SQL Injection prevention, row-level security, data masking, and backup security.

These concepts are critical for every database professional and are widely used in enterprise systems, financial institutions, healthcare platforms, government agencies, and large-scale applications.

---

## 🚀 Coming Up Next: Day 29 – Building a Real-World SQL Project (Spotify) Company Database)

### Topics Covered

- Requirement Gathering
- Database Design
- Table Creation
- Relationships
- Constraints
- Sample Data
- Business Queries
- Reports & Dashboards
- Optimization
- End-to-End Project Implementation

## Progress Status: Day 28 Completed ✅
[PREVIOUS: DAY27-ERROR HANDLING AND DEBUGGING]()👆\
[NEXT: DAY29-BUILDING A REAL WORLD PROJECT]()👇
