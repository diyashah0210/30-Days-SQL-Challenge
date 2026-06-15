# 🚀 30 Days of SQL -- Day 3: Relationships, ER Diagrams & Constraints

 Welcome to **Day 3** of the 30 Days of SQL Challenge!

 In the previous lesson, you learned how to create databases, tables, and insert data. However , real-world databases rarely consist of a single table. Modern database systems contain multiple tables that interact with one another through relationships.

 Today, you\'ll learn how tables are connected, how Entity Relationship (ER) Diagrams help design databases, and how constraints ensure data integrity.

---

 **📚 Table of Contents**

 1\. Why Relationships Matter

 2\. What is an ER Diagram?

 3\. Components of an ER Diagram

 4\. Types of Relationships

 5\. One-to-One Relationship

 6\. One-to-Many Relationship

 7\. Many-to-Many Relationship

 8\. Understanding Constraints

 9\. NOT NULL Constraint

 10\. UNIQUE Constraint

 11\. DEFAULT Constraint

 12\. CHECK Constraint

 13\. AUTO_INCREMENT / IDENTITY

 14\. Practice Exercises

 15\. Key Takeaways

 16\. Day 3 Summary
 
---

 # 1️⃣ Why Relationships Matter

 Imagine storing all information about students, courses, faculty, departments, and fees in a single table.

 **Problems**

 ❌ Duplicate Data

 ❌ Data Inconsistency

 ❌ Difficult Updates

 ❌ Increased Storage Usage\
 Instead, databases divide information into multiple tables and connect
 them through relationships.

 **Benefits**\
 ✅ Reduced Data Redundancy\
 ✅ Improved Data Integrity\
 ✅ Better Database Performance\
 ✅ Easier Maintenance\
 ✅ Scalable Database Designh
 
---

# 2️⃣ What is an ER Diagram?

 **ER Diagram (Entity Relationship Diagram)** is a visual representation of how data is organized and how tables relate to each other .

ER Diagrams are created before developing a database and act as a blueprint for database design.

 **Example ER Diagram**
<img width="625" height="468" alt="image" src="https://github.com/user-attachments/assets/9754c9a1-56f9-45b5-9f03-8c6144b8a97f" />

 This diagram shows that students and courses are related.
---

 # 3️⃣ Components of an ER Diagram

**1. Entities**
An entity represents something that exists independently in the system. Examples include Student, Course, Customer, or Order. In ER diagrams, entities are usually shown as rectangles.

Entities can be:

Strong entities – exist independently (for example, Student)

Weak entities – depend on another entity (for example, Enrolment)
**In SQL, entities become tables.**

 **2. Attribute**
Attributes describe the details of an entity. For example, a Student entity may include attributes such as student_id, name, date_of_birth, and email.

Attributes are typically classified as:

Simple attributes

Composite attributes

Key attributes (such as primary keys)

 **Attributes become columns in a table.**

 **3. Relationship**

Relationships define how entities are connected. They are usually represented using diamonds or labelled lines.

Common relationship types include:

One-to-One

One-to-Many

Many-to-Many

# 4️⃣ Types of Relationships

 Relational databases mainly use three types of relationships:

|  Relationship Type | Description  | Example | Explanation |
| ------------------ | ----------- | ---------- | ---------- |
|  One-to-One | One record relates to one record  | <img width="1003" height="452" alt="image" src="https://github.com/user-attachments/assets/cd623a7f-1a6e-42f2-8c41-de6da899d7e7" />| This means one Country record can map to exactly one Capital record, and one Capital record belongs to exactly one Country 
|  One-to-Many | One record relates to many records | <img width="1313" height="449" alt="image" src="https://github.com/user-attachments/assets/9f4aac9c-cfa5-4f3f-96ca-462c460eb73c" />| This means one Customer record can map to more than one Order record, but one Order record belongs to exactly one Customer
|  Many-to-Many | Many records relate to many records|<img width="825" height="349" alt="image" src="https://github.com/user-attachments/assets/c1fbb8df-f714-4b21-aa9a-ae49539a46f0" />| This means one Author record can map to more than one Book record, and one Book record belongs to many Authors


# 5️⃣ One-to-One Relationship (1:1)

 One record in Table A relates to exactly one record in Table B.

 **Example: Employee and Passport**

 **Employees**

|  employee_id | employee_name |
| ------------ | ------------- |
|  101 | John  |
|  102 | Sarah |

 **Passports**

|  passport_id | employee_id |
| ------------ | ------------- |
|  P001 | 101  |
|  P002 | 102 |

 **Relationship**

|  One Employee → One Passport|
| --------------------------- |

|  One Passport → One Employee  |
| ----------------------------- |

 **ER Representation**

|  Employee 1 \-\-\-\-\-\-\-- 1 Passport  |
| --------------------------------------- |


 **Real-World Examples**

|  • Person ↔ Passport                    |
| --------------------------------------- |

|  • Employee ↔ Laptop                    |
| --------------------------------------- |

|  • Citizen ↔ Aadhaar Card               |
| --------------------------------------- |

---

# 6️⃣ One-to-Many Relationship (1:M)**

 One record in Table A can relate to many records in Table B.

 **Example: Department and Employees**

 **Departments**

|  department_id  | department_name |
| --------------- | --------------- |
|  1 | IT  |
|  2 | HR  |


 **Employees**

|   employee_id     |     employee_name   |    department_id   |
|  ---------------- | ------------------  | ------------------ |
|   101             | John                | 1                  |
|   102             | Sarah               | 1                  |
|   103             | Mike                | 2                  |


 **Relationship**

|  One Department → Many Employees        |
| --------------------------------------- |

|  One Employee → One Department          |
| --------------------------------------- |
 **ER Representation**

|Department 1 \-\-\-\-\-\-\-- M Employee  |
| --------------------------------------- |


 **Why is this Important?**

 Without relationships, department information would have to be repeated for every employee.
---

 # 7️⃣ Many-to-Many Relationship (M:M)

 Multiple records in Table A relate to multiple records in Table B.

 **Example: Students and Courses**

 **Students**

|  student_id | student_name  |
| ----------- | ----------- |
|  101 | Divya              |
|  102 | Aryaman            |

 **Courses**

|  course_id | course_name                |
| ---------- | -------------------------- |
|  1 | SQL                                |
|  2 | Python                             |

 A student can enroll in multiple courses.
 
 A course can have multiple students.

 **Problem**

 This relationship cannot be implemented directly.

 We need a **Junction Table**.

 **Student_Course Table**

|  student_id | course_id    |
| ----------  |  ----------- |
|  101        |      1       |
|  101        |      2       |
|  102        |      1       |                                                           


 **ER Representation**

|  Student M \-\-\-\-\-\-\-- M Course          |
| -------------------------------------------- |

 Implemented as:

|  Student → Student_Course → Course |
| ----------------------------------- |

# 8️⃣ What are Constraints?

 Constraints are rules applied to table columns to ensure valid and reliable data.

 Without constraints, users can insert incorrect or duplicate information.

 **Benefits of Constraints**

 ✅ Improve Data Accuracy

 ✅ Prevent Invalid Entries

 ✅ Maintain Consistency

 ✅ Protect Database Integrity

 ---

# 9️⃣ NOT NULL Constraint

 Ensures a column cannot contain NULL values.

 **Example**


```sql
CREATE TABLE Students (
student_id INT,
student_name VARCHAR(100) NOT NULL);
```                                                                


 **Valid**

```sql
INSERT INTO Students
VALUES (101,'Diya');
```

 **Invalid**

```sql
INSERT INTO Students
VALUES (102,NULL);
```                          

 ❌ Error because the column cannot be empty.

---

# 🔟 UNIQUE Constraint

 Ensures that all values in a column are different.

 **Example**
 
```sql
CREATE TABLE Users (                                                
user_id INT PRIMARY KEY,                                            
email VARCHAR(100) UNIQUE                                           
);
```                                                               

 **Valid**

```sql
 INSERT INTO Users                                                   
 VALUES (1,'diya@gmail.com');                                      
```

 **Invalid**

```sql
 INSERT INTO Users                                                   
 VALUES (2,'diya@gmail.com');                                      
```

 ❌ Duplicate values not allowed.
---

 # 1️⃣1️⃣ DEFAULT Constraint

 Provides a predefined value when none is supplied.
 **Example**

```sql
CREATE TABLE Employees (                                          
employee_id INT,                                                   
city VARCHAR(50) DEFAULT 'Mumbai'                                
);                                                                  
```

 **Insert**

```sql
INSERT INTO Employees(employee_id)  
VALUES (101);
```


 **Result**

|  employee_id | city   |
| ------------ | ------- |
|  101 | Mumbai         |

---

# 1️⃣2️⃣ CHECK Constraint

 Validates data before insertion.

 **Example**

CREATE TABLE Students (                                             
student_id INT,                                                     
age INT CHECK(age \= 18)                                           
);                                                                 

 **Valid**
```sql 
INSERT INTO Students                                                
VALUES (101,22);
```                                                 
 **Invalid**
```sql
INSERT INTO Students                                               
VALUES (102,15);
```                                                 

 ❌ Error because age must be at least 18.

---

 # 1️⃣3️⃣ AUTO_INCREMENT / IDENTITY

 Automatically generates unique IDs.

 **MySQL**

```sql
CREATE TABLE Students (                                             
student_id INT AUTO_INCREMENT PRIMARY KEY,                          
student_name VARCHAR(100)       
);
```                                                

 **Insert**
```sql
INSERT INTO Students(student_name)                                  
VALUES ('Diya');                                                 
```
 Output:

|  student_id | student_name  |
| --------| ------ |
|  1 | Diya |

 **SQL Server**
```sql
student_id INT IDENTITY(1,1)                                        
```
 Where:

 • First value = 1

 • Increment = 1

 # 📝 Practice Exercises

  **Exercise 1**
--
 Create ER diagrams for:

 • Student & Course

 • Employee & Department

 • Customer & Passport

 **Exercise 2**
--
 Identify the relationship type:

 **Scenario A**

 One customer can place many orders.

 **Scenario B**

 One employee has one company laptop.

 **Scenario C**

 Students can enroll in multiple courses.

 **Exercise 3**
--
 Create a table called Employees using:

 • PRIMARY KEY

 • NOT NULL

 • UNIQUE

 • DEFAULT

 **Exercise 4**
--
 Create a table called Students with:

 • AUTO_INCREMENT

 • CHECK(age \= 18)

 Insert 5 sample records.
 
---

# 🎯 Key Takeaways

 ✅ Understood the importance of database relationships

 ✅ Learned the purpose of ER Diagrams

 ✅ Understood Entities, Attributes, and Relationships

 ✅ Learned One-to-One relationships

 ✅ Learned One-to-Many relationships

 ✅ Learned Many-to-Many relationships

 ✅ Understood NOT NULL constraint

 ✅ Understood UNIQUE constraint

 ✅ Understood DEFAULT constraint

 ✅ Understood CHECK constraint

 ✅ Learned AUTO_INCREMENT / IDENTITY

 # 📖 Day 3 Summary

 Today, you learned how relational databases organize information across multiple tables using relationships. You explored ER Diagrams a a planning tool for database design and studied the three major relationship types used in real-world applications. You also learned how constraints help maintain data quality and prevent invalid records from entering the database. 
 
These concepts form the foundation of database design and are essential
before moving into advanced querying techniques.

## 🚀 Coming Up Next: Day 4 – SQL Command Categories & The Library Analogy

So far, you've learned how to create databases, design tables, establish relationships, and maintain data integrity using constraints.

Before writing complex queries, it's important to understand how SQL commands are classified and what purpose each category serves.

In Day 4, you'll learn:

### SQL Command Categories

* DDL (Data Definition Language)
* DML (Data Manipulation Language)
* DQL (Data Query Language)
* DCL (Data Control Language)
* TCL (Transaction Control Language)

### The Library Management Analogy

Understand SQL using a real-world library system where:

* Creating shelves represents DDL
* Adding books represents DML
* Searching books represents DQL
* Managing librarian permissions represents DCL
* Borrowing and returning books safely represents TCL

### First Deep Dive: DDL Commands

You'll begin exploring:

```sql
CREATE
ALTER
DROP
TRUNCATE
RENAME
```

and learn how database structures are created and managed in professional database systems.

## Progress Status: Day 3 Completed ✅
---
[PREVIOUS: DAY2](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/fbf25153dfae9f6150f106e9887d44facf0c82fd/DAY2/DAY2-CREATE%20statement.md)👆\
[NEXT DAY4](https://github.com/diyashah0210/30-Days-SQL-Challenge/blob/681deea889938d53ac6918ecf559edfb86086dd0/DAY4/DAY4-SQL%20Command%20Categories%20%26%20Introduction%20to%20DDL.md)👇
