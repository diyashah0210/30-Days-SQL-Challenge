 # 🚀 30 Days of SQL -- Day 4: SQL Command Categories & Introduction to DDL

 Welcome to **Day 4** of the 30 Days of SQL Challenge!

 So far , you\'ve learned about databases, tables, data types, keys,r elationships, ER diagrams, and constraints. Before diving deeper into writing complex queries, it\'s important to understand how SQL commands are organized.

 Just as a library has different activities such as creating shelves, adding books, searching for books, managing librarian access, and handling book transactions, SQL commands are divided into categories based on their purpose.

 In this lesson, you\'ll learn the different categories of SQL commands and take your first deep dive into **Data Definition Language (DDL)**.

 **📚 Table of Contents**

 1\. Why SQL Commands are Categorized

 2\. The Library Management Analogy

 3\. SQL Command Categories Overview

 4\. Data Definition Language (DDL)

 5\. CREATE Command

 6\. ALTER Command

 7\. DROP Command

 8\. TRUNCATE Command

 9\. RENAME Command

 10\. DDL Command Comparison

 11\. Practice Exercises

 12\. Key Takeaways

 13\. Day 4 Summary

 # 1️⃣ Why SQL Commands are Categorized

 Imagine managing a library.

 Different tasks are performed every day:

 • Constructing shelves

 • Adding books

 • Searching books

 • Managing librarian permissions

 • Processing borrow and return transactions

 It would be inefficient if every task used the same process.

 Similarly, SQL organizes commands into categories based on what they do.

 This classification makes databases easier to understand, manage, and maintain.

----

 # 2️⃣ Library Management Analogy

 Think of SQL as a digital library management system.


| SQL Category      |  Library Activity |
| ----------------- | ----------------- |
|  DDL | Creating library rooms and shelves and labelling the sections      |
|  DML | Adding new books to the shelves or checking them out               |
|  DQL | Searching specific books from the library                          |
|  DCL | Managing librarian permissions like a key to the "rare book" but not to everyone |
|  TCL | Borrowing and returning books safely, deciding to "save" the library log or "Undo" a mistake.  |

 This analogy will help you understand the purpose of each SQL command category.

 ---

 # 3️⃣ SQL Command Categories Overview

 SQL commands are broadly divided into five categories.

 SQL\
 ├── DDL (Data Definition Language)\
 │ ├── CREATE\
 │ ├── ALTER\
 │ ├── DROP\
 │ ├── TRUNCATE\
 │ └── RENAME\
 ├── DML (Data Manipulation Language)\
 │ ├── INSERT\
 │ ├── UPDATE\
 │ └── DELETE\
 ├── DQL (Data Query Language)\
 │ └── SELECT\
 ├── DCL (Data Control Language)\
 │ ├── GRANT\
 │ └── REVOKE                                                       
 └── TCL (Transaction Control Language)                              
  ├── COMMIT                                                          
  ├── ROLLBACK                                                        
  └── SAVEPOINT                                                       

 ### DDL -- Data Definition Language

It is all about the "Blue-print", we are going to master the commands that create, change, and destroy the structure of our databases.

The commands are as follows:

 • CREATE

 • ALTER

 • DROP

 • TRUNCATE

 • RENAME

 ### DML -- Data Manipulation Language

 Used to manipulate records inside tables.

 Examples:

 • INSERT

 • UPDATE

 • DELETE

 ### DQL -- Data Query Language

 Used to retrieve data.

 Example:

 • SELECT

 ### DCL -- Data Control Language

 Used to manage permissions and security.

 • GRANT

 • REVOKE

 ### TCL -- Transaction Control Language

 Used to manage transactions.

 Examples:

 • COMMIT

 • ROLLBACK

 • SAVEPOINT
 
---
 # 4️⃣ Understanding DDL (Data Definition Language)

 DDL stands for **Data Definition Language**.

 It is responsible for creating and managing database structures.

 Think of DDL as the construction team of a library.

 Before books can be stored:

 • The building must exist.

 • Shelves must be installed.

 • Sections must be created.

 Similarly, before data can be inserted:

 • Databases must exist.

 • Tables must exist.

 • Columns must be defined.

---
 # 5️⃣ CREATE Command


 The CREATE command is used to create database objects.

 **Creating a Database**

```sql
 CREATE DATABASE LibraryDB;                                          
```

 **Result**

 A new database named **LibraryDB** is created.

 **Using the Database**
```sql
 USE LibraryDB;                                                    
```
 This tells SQL that all future operations will occur inside LibraryDB.

 **Creating a Table**

 ```sql
 CREATE TABLE Books (                                                
 book_id INT PRIMARY KEY,                                            
 title VARCHAR(100),                                                 
 author VARCHAR(100)                                                 
 );     
 ```                                                           

 **Table Structure**

|  Column | Data Type   | Keys |
| -------- | ---------- | ----- |
|  book_id | INT        | PRIMARY KEY |
|  title | VARCHAR(100)  |   ---  |
|  author | VARCHAR(100)   |  ---  |

---
 # 6️⃣ ALTER Command

 The ALTER command modifies an existing table structure.

 **1. Adding a New Column**

```sql
 ALTER TABLE Books                                                   
 ADD price DECIMAL(10,2);    
```                                 

 **Updated Table**

|  Column | Data Type  |
| ------- | -------- |
|  book_id | INT     |
|  title | VARCHAR(100) |
|  author | VARCHAR(100)   |
|  price | DECIMAL(10,2)   |

 **2. Modifying a Column**
```sql 
  ALTER TABLE Books                                                   
  MODIFY title VARCHAR(200);       
```                                   
|  Column | Data Type  |
| ------- | -------- |
|  book_id | INT     |
|  title | VARCHAR(200) |
|  author | VARCHAR(100)   |
|  price | DECIMAL(10,2)   |

 This increases the title column size from 100 to 200 characters.
 
---

 # 7️⃣ DROP Command

 The DROP command permanently removes a database object.

 **Drop a Table**
```sql
  DROP TABLE Books;                                                   
```
 **Result** 

 ❌ Table deleted permanently.

 ❌ All records lost.

 ⚠️ Use carefully because the operation cannot be reversed.

 **Drop a Database**

```sql
 DROP DATABASE LibraryDB;         
 ```                                   

 This removes the entire database and everything inside it.

---
 # 8️⃣ TRUNCATE Command
 TRUNCATE removes all records from a table but keeps the table structure.

 **Example**
 Before:

|  book_id | title          |
| ---------- | ------------ |
|  1|  SQL Basics           |
|  2 | Python Fundamentals  |

 Execute:

```sql
  TRUNCATE TABLE Books;       
```                                        

 After:


|  book_id | title |
| ------- | ------ |
|         |        |

 The table still exists, but all rows are removed.

 **Difference Between DELETE and TRUNCATE**

|  DELETE | TRUNCATE                        |
| -------- | ------------------------------ |
|  Removes selected rows| Removes all rows  |
|  Can use WHERE clause | Cannot use WHERE clause  |
|  Slower|  Faster                                 |
|  Structure remains | Structure remains           |

---
# 9️⃣ RENAME Command 
Used to change the name of a database object.

 **Rename a Table**

```sql 
 RENAME TABLE Books TO LibraryBooks;        
```

 **Before**

|  Books       |
| ------------ |

 **After**

|  LibraryBooks |
| ------------- |

 The data remains unchanged.

---
 # 🔟 DDL Command Comparison

|  Command | Purpose |
| -------- | -------- |
|  CREATE | Create database objects    |
|  ALTER | Modify existing objects     |
|  DROP | Remove objects permanently   |
|  TRUNCATE | Remove all records       |
|  RENAME | Change object names        |

---

 ## 📝 Practice Exercises
---
### Exercise 1

 Create a database called:

```sql
CREATE DATABASE CollegeDB;                                    
```

### Exercise 2

 Create a table called Students containing:

 • student_id

 • student_name

 • age

### Exercise 3
 Add a new column called email using ALTER.

### Exercise 4
 Rename the Students table to CollegeStudents.

### Exercise 5
 Insert sample data and then use TRUNCATE to remove all records.

### Exercise 6
 Create a temporary table and delete it using DROP.

 # 🎯 Key Takeaways
 ✅ SQL commands are divided into categories based on functionality
 DDL is used to define database structures\
 ✅ CREATE creates databases and tables\
 ✅ ALTER modifies existing structures\
 ✅ DROP permanently removes objects\
 ✅ TRUNCATE removes all records while keeping the table\
 ✅ RENAME changes object names\
 ✅ Understanding DDL is essential before working with data

 # 📖 Day 4 Summary
 Today, you learned how SQL commands are categorized and why these categories exist. Using the library management analogy, you explored how different SQL operations serve different purposes. You also took a detailed look at Data Definition Language (DDL) and learned how to create, modify, delete, truncate, and rename database objects.

Understanding DDL is a foundational skill because every database begin with well-designed structures

 before any data can be stored or analyzed.

 # 🚀 Coming Up Next: Day 5 -- Data Manipulation Language (DML)

 You\'ll learn how to work with actual data using:

  INSERT                                                              
  UPDATE                                                              
  DELETE                                                              

 and understand how records are added, modified, and removed from database tables.
 
---

 ## Progress Status: Day 4 Completed ✅
---
[PREVIOUS: DAY3](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/80eebed46948b8e5ab416a710eb39a73795d2a04/DAY3/DAY3-Relationships%2C%20ER%20Diagrams%20%26%20Constraints.md)👆\
[NEXT: DAY 5](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/80eebed46948b8e5ab416a710eb39a73795d2a04/DAY5/DAY5-%20DML%20%26%20DQL%20Fundamentals.md)👇
