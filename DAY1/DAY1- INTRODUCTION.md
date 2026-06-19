 # 30 Days of SQL
 
  ![SQL-BANNER](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/f041d7eaf22d325805abb71fa0114eff23d40f8e/DAY1-INTRODUCTION/Intropage.png)
 
 # 30 DAYS SQL CHALLENGE -- Day 1: Foundations of Databases and SQL
 **Welcome to Day 1**

 Welcome to the first day of your SQL learning journey. Before writing
 complex queries or analyzing large datasets, it is important to
 understand the fundamentals of databases, how data is stored, and why
 SQL is one of the most valuable skills in the technology and analytics
 industry.

 By the end of today, you will:

 • Understand what SQL is and why it is used.

 • Learn the role of databases in modern applications.

 • Differentiate between relational and non-relational databases.• Set
 up a SQL environment for practice.

 • Execute your first SQL statement.

 # 1. Understanding SQL

 **What is SQL?**

 **SQL (Structured Query Language)** is a standardized language used to
 communicate with relational databases. It enables users to store,
 retrieve, modify, and manage data efficiently.

 **Common Uses of SQL**

 • Retrieving information from databases\
 • Adding new records\
 • Updating existing records\
 • Removing unwanted data\
 • Creating and modifying database structures\
 • Managing user permissions and access control

 **Popular Database Systems Using SQL**

 • MySQL\
 • PostgreSQL\
 • SQLite\
 • Microsoft SQL Server\
 • Oracle Database\
 • MariaDB

 # 2. Why SQL Matters

SQL is considered a core skill across multiple industries because data
is at the center of decision-making

 and software systems.

 **Career Paths That Use SQL**

 • Data Analyst

 • Data Scientist

 • Business Analyst

 • Database Administrator

 • Software Engineer

 • Backend Developer

 • Machine Learning Engineer

 **Benefits of Learning SQL**

 • Easy to learn and widely adopted

 • Essential for working with data

 • Used by organizations of all sizes

 • High demand across industries

 • Forms the foundation for advanced analytics and data engineering

 # 3. Prerequisites

 No prior database experience is required.

 **Recommended Knowledge**

 • Basic computer operations

 • Familiarity with software installation

 • Basic understanding of programming concepts (optional)

 **Tools Required**

 Choose any one of the following environments:

1.  MySQL: Workbench Beginners and professionals                         
2. PostgreSQL: Advanced database applications                           
3. SQLite:  Lightweight practice projects                                
4. SQL Server Enterprise environments                                  
5. Online SQL Editors Quick learning without installation              


# 4. Setting Up Your SQL Environment

## **SQL Installation Guide**

Before diving into SQL, it’s important to set up a SQL environment on your system. Below are the installation instructions for various popular SQL database management systems.

### **1. MySQL Installation**

#### **Windows**
1. Download MySQL Installer from the [official website](https://dev.mysql.com/downloads/installer/).
2. Run the installer and follow the installation wizard. Choose "Developer Default" to install MySQL Server and MySQL Workbench.
3. Set a root password when prompted during installation.
4. Complete the installation and launch MySQL Workbench to interact with your database.

#### **macOS**
1. Download MySQL DMG Archive from the [official website](https://dev.mysql.com/downloads/mysql/).
2. Follow the instructions to install it.
3. Open `System Preferences` and click on the MySQL icon to start the server.
4. Use the Terminal to access the MySQL server by typing `mysql -u root -p`.

#### **Linux (Ubuntu/Debian)**
1. Open a terminal and run:
   ```bash
   sudo apt update
   sudo apt install mysql-server
   ```
2. Secure your MySQL installation:
   ```bash
   sudo mysql_secure_installation
   ```
3. After installation, log into MySQL using:
   ```bash
   sudo mysql -u root -p
   ```


### **2. PostgreSQL Installation**

#### **Windows**
1. Download the PostgreSQL installer from [EnterpriseDB](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads).
2. Run the installer and follow the on-screen instructions.
3. Set a password for the default `postgres` role.
4. Open **pgAdmin** or use the command line to interact with your database.

#### **macOS**
1. Install PostgreSQL using [Homebrew](https://brew.sh/):
   ```bash
   brew install postgresql
   ```
2. Start the PostgreSQL service:
   ```bash
   brew services start postgresql
   ```
3. Access PostgreSQL through the terminal:
   ```bash
   psql postgres
   ```

#### **Linux (Ubuntu/Debian)**
1. Open a terminal and install PostgreSQL:
   ```bash
   sudo apt update
   sudo apt install postgresql postgresql-contrib
   ```
2. Switch to the PostgreSQL user:
   ```bash
   sudo -i -u postgres
   ```
3. Access PostgreSQL:
   ```bash
   psql
   ```


### **3. SQLite Installation**

SQLite is a lightweight, file-based SQL database, useful for smaller projects or testing.

#### **Windows**
1. Download the precompiled binaries from [SQLite Downloads Page](https://www.sqlite.org/download.html).
2. Extract the downloaded file and place it in a folder (e.g., `C:\sqlite`).
3. Add the SQLite directory to your system’s PATH for easy access.
4. Open Command Prompt and type `sqlite3` to interact with SQLite.

#### **macOS**
1. SQLite is pre-installed on macOS. Open Terminal and type:
   ```bash
   sqlite3
   ```

#### **Linux (Ubuntu/Debian)**
1. Install SQLite via the terminal:
   ```bash
   sudo apt update
   sudo apt install sqlite3
   ```
2. Run SQLite:
   ```bash
   sqlite3
   ```


### **4. SQL Server Installation (Microsoft SQL Server)**

#### **Windows**
1. Download the SQL Server installer from the [Microsoft website](https://www.microsoft.com/en-us/sql-server/sql-server-downloads).
2. Run the installer and choose "Basic" or "Custom" installation.
3. Set up your SQL Server instance and authentication settings.
4. Use **SQL Server Management Studio (SSMS)** to manage your databases.

#### **macOS** (Using Docker)
1. Install Docker for macOS from the [Docker website](https://www.docker.com/products/docker-desktop).
2. Pull the SQL Server Docker image:
   ```bash
   docker pull mcr.microsoft.com/mssql/server
   ```
3. Run the SQL Server container:
   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=YourPassword123' -p 1433:1433 --name sql_server_container -d mcr.microsoft.com/mssql/server
   ```
4. Use a SQL client like Azure Data Studio or connect via `sqlcmd` to manage your database.


### **5. Oracle Database Installation**

#### **Windows/macOS/Linux**
1. Download Oracle Database Express Edition (XE) from the [Oracle website](https://www.oracle.com/database/technologies/appdev/xe.html).
2. Follow the instructions to install it based on your operating system.


### **6. MariaDB Installation**

MariaDB is a community-driven fork of MySQL, often used as a drop-in replacement for MySQL.

#### **Windows**
1. Download the MariaDB installer from the [official website](https://mariadb.org/download/).
2. Run the installer and follow the installation wizard.
3. Set a root password and configure MariaDB as required.

#### **macOS**
1. Install MariaDB using [Homebrew](https://brew.sh/):
   ```bash
   brew install mariadb
   ```
2. Start MariaDB:
   ```bash
   brew services start mariadb
   ```

#### **Linux (Ubuntu/Debian)**
1. Install MariaDB from the terminal:
   ```bash
   sudo apt update
   sudo apt install mariadb-server
   ```
2. Secure MariaDB:
   ```bash
   sudo mysql_secure_installation
   ```


Once you've selected your SQL database system and followed the installation instructions, you’ll be ready to begin writing and executing SQL queries. Make sure to confirm that everything is set up correctly by testing your installation with a simple SQL query!


## 🚀 What You'll Learn Today


# 5. Introduction to Databases

 **What is a Database?**

A database is an organized collection of data designed for efficient
storage, retrieval, and management.

 **Examples**

 • Banking systems

 • E-commerce websites

 • Social media platforms

 • Hospital management systems

 • Student information systems

# 6. Types of Databases

 **Relational Databases (SQL)**

 Data is stored in structured tables consisting of rows and columns.

 **Examples**

 • MySQL

 • PostgreSQL

 • Oracle

 • SQL Server

 **Characteristics**

 • Structured format

 • Relationships between tables

 • Uses SQL language

 • High data consistency

 **Non-Relational Databases (NoSQL)**

 Data is stored in flexible formats such as documents, key-value pairs,
 graphs, or wide-column

 structures.

 **Examples**

 • MongoDB

 • Cassandra

 • Redis

 **Characteristics**

 • Flexible schemas

 • High scalability

 • Suitable for large distributed systems

# 7. Core Database Concepts

 **Table**

 A table stores related information.

 **Row (Record)**

 A single entry within a table.

 **Column (Field)**

 Represents a specific attribute.

 Examples:

 • Employee_ID

 • Name

 • Department


 **Primary Key**\
 A unique identifier for each record in a table.

 No two employees should have the same Employee_ID.

 **Data Types**\
 Data types define what kind of information can be stored.


 # 8. Your First SQL Statement

```sql 
SELECT \* FROM table_name;   
```                                      


 **First Practice Query**
```sql
SELECT \'Hello, SQL!\';   
```                                          
 **Expected Output**
```sql
Hello, SQL!                                                         
```
 Congratulations! You have executed your first SQL query.

 # 9. Day 1 Activities

 **Activity 1: Explore SQL**

 Research:

 • What SQL stands for

 • Where SQL is used

 • Popular database systems

 **Activity 2: Install a Database Tool**

 Choose one:

 • MySQL

 • PostgreSQL

 • SQLite

 • SQL Server

 Verify successful installation by opening the tool.

 **Activity 3: Execute a Query**

 Run:

```sql
SELECT \'Hello, SQL!\'; 
```

 Capture a screenshot of the result for your learning portfolio.
**SCREENSHOT**
<img width="959" height="503" alt="image" src="https://github.com/user-attachments/assets/8c410f6d-529d-489a-8baa-ada2578a7c7c" />

 **Activity 4: Understand Database Components**

 Identify:

 • Table

 • Row

 • Column

 • Primary Key

 • Data Type

 using a sample student or employee database.

 # 10. Key Learnings from Day 1

 By completing Day 1, you should now understand:

 • What SQL is and why it is important

 • The purpose of databases

 • Differences between SQL and NoSQL databases

 • Basic database terminology

 • How to set up a SQL environment

 • How to execute a simple SQL statement

 # Beginner-Friendly Tutorials- **Additional Learning Resources**
- [W3Schools SQL Tutorial](https://www.w3schools.com/sql/)
- [SQLZoo Interactive Tutorial](https://sqlzoo.net/)
- [Learn SQL on Codecademy](https://www.codecademy.com/learn/learn-sql)

 # Day 1 Summary

 Today focused on building a strong foundation in SQL and database
 concepts. You explored the

 purpose of databases, learned essential terminology, set up a working
 SQL environment, and executed

 your first SQL query. These concepts will serve as the building blocks
 for everything that follows in this

 30-day SQL learning program.

 **Coming Up Next: Day 2 -- Data Definition Language (DDL)**

 You will learn how to create, modify, and delete database objects
 using commands such as:

```sql 
CREATE  
ALTER 
DROP  
TRUNCATE                                                 
```

## Progress Status: Day 1 Completed ✅

[NEXT: DAY2-CREATE STATEMENT](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/main/DAY2/DAY2-CREATE%20statement.md) 👆
