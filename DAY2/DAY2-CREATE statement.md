

 # 🚀 30 Days of SQL -- Day 2 
 
 ## Creating Databases, Tables, Data Types, Keys, INSERT & SELECT

 Welcome to **Day 2** of the **30 Days of SQL Challenge**!

 In Day 1, you learned the fundamentals of SQL, databases, and how relational databases work. Today, we\'ll take the next step by creating our own database, 
 designing tables, understanding data types and keys, inserting data, and finally retrieving that data using SQL
 queries.
 By the end of this lesson, you\'ll be able to:
 
 • Create a database
 
 • Create tables inside a database
 
 • Understand SQL data types
 
 • Learn about keys and their importance
 
 • Insert records into tables
 
 • Retrieve data using SELECT statements
 
 ---

 # 📚 Table of Contents

 1\. Introduction

 2\. Creating a Database

 3\. Using a Database

 4\. Understanding Data Types

 5\. Understanding Keys

 6\. Creating Your First Table

 7\. Inserting Data with INSERT

 8\. Retrieving Data with SELECT

 9\. Practice Exercises

 10\. Key Takeaways

 11\. Day 2 Summary

 ---

 # 1️⃣ Introduction

 Before storing data, we need a place where the data can live.
 The hierarchy in SQL looks like this:
|Database|
|------------------------------------| 

   ↓ 

|Tables|
|------------------------------------| 

↓  

|Columns|
|------------------------------------| 

↓

|Rows(Records)|
|------------------------------------| 

 A database contains multiple tables, and each table stores related information.

---

 # 2️⃣ Creating a Database

 A database is a container that stores tables, views, procedures, and
 other database objects.

 **Syntax**
```sql
CREATE DATABASE database_name
```

 **Example**

```sql
CREATE DATABASE SchoolDB;
```                                          
 **Explanation**
CREATE DATABASE tells SQL to create a new database. SchoolDB  is the name of the database.

 After execution, a new database named **SchoolDB** will be created.

 ---

 # 3️⃣ Using a Database

 Before creating tables, we need to select the database in which we
 want to work.

 **Syntax**

```sql
USE database_name; 
``` 

 **Example**

```sql
USE SchoolDB; 
```                                                     
 **Explanation**\
 This command tells SQL that all upcoming operations should be
 performed inside the **SchoolDB** database.

---

# 4️⃣ Understanding SQL Data Types 
Data types define the kind of values that can be stored in a column.
Choosing the correct data type improves storage efficiency and data accuracy.
 **Common SQL Data Types**
|  Data Type         |  Description       | Example      |
| -----------------  | ------------------ |--------------|
|  INT               | Stores whole numbers        | 25          |
|  VARCHAR(n)        |  Stores text values       | \'Diya\'    |
|  DATE              |  Stores dates      | \'2025-06-04\'|
| DECIMAL(10,2)      |  Stores decimal numbers    | 99.99       |
|  FLOAT             |  Stores approximate decimal values          | 3.14159     |
|  BOOLEAN           |  Stores TRUE/FALSE values | TRUE        |
| CHAR(n)            |  Fixed-length text | \'A\'       |
|  DATETIME          |  Stores date and time   | \'2025-06-04 10:30:00\'|


 **Data Type Examples**\
 **Integer**
  Stores whole numbers.
```sql
age INT                        
```

|  18          |
|--------------|
|  1500        |
|  300000000   |

 **Text**
 Stores text values up to 100 characters.
```sql
name VARCHAR(100)
```
 Examples:
|   Ron                              |
|------------------------------------|
|  Harry                             |
|  Emma                              |

 **Date**
```sql
enrollment_date   DATE
```
 Example:
| 2025-06-04 |
|------------------------------------|

 **Decimal**
```sql
price DECIMAL(10,2)
```
 Example:
|  499.99     |
|-------------|
|  1499.50    |

---

 # 5️⃣ Understanding Keys
 Imagine having this table  to wor with: 
 | Roll No. | Name |
 | --- | ---- |
 | 101 | Aakash |
 | 102 | Aakash |
 | 103 | Aakash |
 
 As we can observe here that there are 3 Aakash while we can only segregate them using Roll No. which is labelled to be Keys.
 
 Keys help identify records uniquely and establish relationships between tables. Without keys, managing and linking data becomes
 difficult.
 Further ahead we will also learn about different types of relationships and how are they establish w.r.t tables.

 ### **Primary Key**
 A Primary Key uniquely identifies every record in a table.

 **Example**

```sql
student_id INT PRIMARY KEY
```
|  student_id |student_name |
| ---------   | ------------|
|  101 | Ron |
|  102 |Harry  |
|  103| Emma  |

 ### **Rules**

 • Must contain unique values

 • Cannot contain NULL values

 • Only one Primary Key per table

 ### **Foreign Key**

 A Foreign Key creates a relationship between two tables.

 **Example**
```sql
FOREIGN KEY (student_id)
```
```sql
REFERENCES Students(student_id) 
```
 Used to connect records across multiple tables.

 ### **Candidate Key**

 A column that can potentially become a Primary Key.

 **Example**
 • Email
 • Passport Number
 • Employee ID
 
 ### **Composite Key**

 A combination of two or more columns that uniquely identifies a record.

 **Example**
```sql
PRIMARY KEY(student_id, course_id)
```    

 ### **Super Key**

 A set of one or more columns capable of uniquely identifying records.
 Example:

| Student_ID |
|------------|

|Student_ID + Name|
|-----------------|                                                 

|Student_ID + Email|                                                 
|------------------|

### **DIFFERENCE BETWEEN THE KEYS**
| Keys | Modify values? | NULL Values? | Duplicate Values? |
|----- | -------------- | ------------ | ----------------- |
|Primary| ❌ | ❌ | ❌|
|Candidate| ❌| ❌| ❌ |
|Composite| - | - | - |
|Unique| ❌ | ✅ | ❌ |
|Foreign| ✅| ✅ | ✅ |

---

# 6️⃣ Creating Your First Table

 Now let\'s create a table called **Students**.

 **Syntax**
```sql
CREATE TABLE table_name (column_name datatype constraints);   
```                                                              
 **Example**

```sql
CREATE TABLE Students (student_id INT PRIMARY KEY,student_name VARCHAR(100) NOT NULL, age INT,enrollment_date DATE);                                                                  
```
 **Table Structure**

| Column            | Data Type          |  Constraint         |
|-----------------  | -----------------  | ------------------- |
|   student_id      | INT                | PRIMARY KEY         |
|   student_name    |  VARCHAR(100)      | NOT NULL            |
|   age             | INT                | None                |
|  enrollment_date  |  DATE              | None                |


 **Explanation**

 **student_id**

```sql 
student_id INT PRIMARY KEY
```


 • Unique identifier\
 • Cannot be duplicated

 **student_name**


```sql 

student_name VARCHAR(100) NOT NULL                                  
```


 • Stores student names\
 • Cannot be left empty

 **age**


```sql 
age INT                                                             
```


 Stores age values.

 **enrollment_date**

```sql 
enrollment_date DATE                                                
```
 Stores admission dates.

---

# 7️⃣ Inserting Data with INSERT

 After creating a table, we need to add records.

 The INSERT statement is used to add data into a table.

 **Insert a Single Record**

```sql
INSERT INTO Students VALUES (101, \'Ron\', 23, \'2025-06-04\');
```



 **Insert Multiple Records**
```sql
INSERT INTO Students VALUES (102, \'Harry\', 24, \'2025-06-05\'),
(103, \'Emma\', 22, \'2025-06-06\');
```


 **Current Table Data**


|  student_id    | student_name| age           |  enrollment_date |
|--------------  | ----------  | ------------- | ---------------- |
|   101         | Ron          | 23            | 2025-06-04       |
|   102         | Harry        | 24            | 2025-06-05       |
|   103         | Emma         | 22            | 2025-06-06       |

---

 # 8️⃣ Retrieving Data with SELECT

 The SELECT statement is used to retrieve data from a table.

 **Retrieve All Columns**
```sql
 SELECT \*  FROM Students;    
```
 **Output**



|  student_id    | student_name| age           |  enrollment_date |
|--------------  | ----------  | ------------- | ---------------- |
|   101         | Ron          | 23            | 2025-06-04       |
|   102         | Harry        | 24            | 2025-06-05       |
|   103         | Emma         | 22            | 2025-06-06       |

 **Retrieve Specific Columns**


```sql
SELECT student_name, age    
FROM Students;
```

 **Output**

| student_name | age        | 
|------------- | ---------- | 
| Ron          | 23         | 
| Harry        | 24         | 
| Emma         | 22         | 


 **📝 Practice Exercises**

 **Exercise 1**\
 Create a database named:


| LibraryDB |
| --------- |


 **Exercise 2**\
 Create a table named **Books** with the following columns:

 • book_id\
 • title\
 • author\
 • price

 **Exercise 3**\
 Insert at least 3 records into the Books table.

 **Exercise 4**\
 Display all records using:
```sql
SELECT \* 
FROM Books;
```


 **Mini Challenge**\
 Create a table called **Employees** containing:\
 • employee_id\
 • employee_name\
 • department\
 • salary\
 Insert 5 records and display the results.

 **🎯 Key Takeaways**\
 By completing Day 2, you have learned:\
 ✅ How to create a database\
 ✅ How to use a database\
 ✅ SQL data types and their usage\
 ✅ Different types of keys\
 ✅ How to create tables\
 ✅ How to insert records\
 ✅ How to retrieve records using SELECT

 **📖 Day 2 Summary**\
 Today, you built your first database from scratch. You learned how
 databases store information, how tables are created, how data types
 define the nature of stored data, and why keys are essential for
 maintaining data integrity. You also inserted records into a table and
 retrieved them using SELECT statements.

 These concepts form the foundation of all future SQL operations and
 are essential for database design, querying, and data analysis.

 **🚀 Coming Up Next: Day 3 -- Constraints and Advanced INSERT
 Operations**\
 Tomorrow you\'ll learn:\
• Relations between tables

• Constraints related to the INSERT techniques:NOT NULL,UNIQUE,DEFAULT,CHECK,AUTO_INCREMENT / IDENTITY

• Advanced INSERT techniques

---

 ## **Progress Status:** Day 2 Completed ✅
 
 ---
[ PREVIOUS: DAY-1](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/bd613df4a3f8ccf85fb37de3bcdd19464ff16e8b/DAY1-INTRODUCTION/README.md)👆\
[NEXT: DAY-3](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/bd613df4a3f8ccf85fb37de3bcdd19464ff16e8b/DAY3/DAY3-Relationships%2C%20ER%20Diagrams%20%26%20Constraints.md)👇
