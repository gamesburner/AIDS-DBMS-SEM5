## 📝 SQL DDL and DML Demonstration Practical

This document explains the steps executed in the MySQL Command Line Interface (CLI) to demonstrate the usage of SQL Data Definition Language (DDL) and Data Manipulation Language (DML) statements.

-----

## 🎯 Practical Title

**Design and Develop SQL DDL Statements which demonstrates use of SQL objects such as Table, View, Index, Sequence, Synonym, and different Constraints, etc.**

**(Note: This demonstration focuses primarily on basic Table creation and DML operations (INSERT, SELECT, UPDATE, DELETE), along with simple `ALTER TABLE` and aggregate functions, as reflected in the provided MySQL session log.)**

-----

## 🛠️ Environment

  * **Database System:** MySQL Community Server (Version 8.3.0)
  * **Interface:** MySQL Command Line Client

-----

## 💻 Steps Performed in MySQL CLI

The following steps were executed to set up the database, create a table, and perform various data manipulation and structure modification operations.

### 1\. Database Initialization

This section focuses on connecting to the MySQL server and setting up the working database.

  * **Create Database:** The `practical` database was created to house the demonstration tables.
    ```sql
    mysql> CREATE DATABASE practical;
    ```
  * **Select Database:** The newly created database was selected as the active database for subsequent operations.
    ```sql
    mysql> USE practical;
    ```

### 2\. Table Creation and Initial Data Insertion (DML)

A basic table named `stud` (student) was created, and initial data was populated.

  * **Create Table:** The `stud` table was created with four columns: `rno` (Roll Number), `name`, `age`, and `marks`.
    ```sql
    mysql> CREATE TABLE stud(rno INT, name VARCHAR(20), age INT, marks INT);
    ```
  * **Initial Data Insertion:** Five rows of sample data were inserted into the `stud` table.
    ```sql
    mysql> INSERT INTO stud(rno,name,age,marks) VALUES(1,'john',18,89);
    mysql> INSERT INTO stud(rno,name,age,marks) VALUES(2,'Jay',18,89);
    mysql> INSERT INTO stud(rno,name,age,marks) VALUES(3,'sakshi',17,84);
    mysql> INSERT INTO stud(rno,name,age,marks) VALUES(4,'sanket',20,56);
    mysql> INSERT INTO stud(rno,name,age,marks) VALUES(5,'pooja',19,96);
    ```
  * **Verification:** The inserted data was retrieved and displayed.
    ```sql
    mysql> SELECT * FROM stud;
    ```

### 3\. Data Manipulation Operations (DML)

Data within the table was modified and queried using DML commands.

  * **Update:** The `age` of the student with `rno=3` was updated from 17 to 19.
    ```sql
    mysql> UPDATE stud SET age=19 WHERE rno=3;
    ```
  * **Delete:** The record for the student with `rno=5` was removed from the table.
    ```sql
    mysql> DELETE FROM stud WHERE rno=5;
    ```
  * **Selective Query (`LIKE`):**
      * Find students whose name starts with 's'.
        ```sql
        mysql> SELECT * FROM stud WHERE name LIKE 's%';
        ```
      * Find students whose name ends with 'i'.
        ```sql
        mysql> SELECT * FROM stud WHERE name LIKE '%i';
        ```
  * **Aliasing and Sorting (`AS`, `ORDER BY`):**
      * Display the `name` column with an alias `student_Name`.
        ```sql
        mysql> SELECT name AS student_Name FROM stud;
        ```
      * Display the student names sorted alphabetically.
        ```sql
        mysql> SELECT name AS student_Name FROM stud ORDER BY name;
        ```

### 4\. Table Structure Modification (DDL) and Further DML

An existing table was modified using a DDL command, followed by more data insertions.

  * **Alter Table (DDL):** A new column, `city` (VARCHAR(20)), was added to the `stud` table.
    ```sql
    mysql> ALTER TABLE stud ADD COLUMN city VARCHAR(20);
    ```
  * **New Data Insertion:** Several new rows were inserted, some demonstrating data integrity issues (duplicate `rno=6`) and others including the new `city` column data.
    ```sql
    mysql> INSERT INTO stud(rno,name,age,marks) values(6,'abhi',19,87);
    mysql> INSERT INTO stud(rno,name,age,marks) values(6,'soham',21,68);
    mysql> INSERT INTO stud(rno,name,age,marks,city) values(7,'sora',21,68,'nashik');
    mysql> INSERT INTO stud(rno,name,age,marks,city) values(8,'pooja',23,53,'pune');
    ```
  * **Final Verification:** Display all data including the new `city` column (which is `NULL` for older records).
    ```sql
    mysql> SELECT * FROM stud;
    ```

### 5\. Aggregate Functions

Standard SQL aggregate functions were used to summarize the data.

  * **Maximum Marks:**
    ```sql
    mysql> SELECT MAX(marks) FROM stud;
    ```
  * **Minimum Marks:**
    ```sql
    mysql> SELECT MIN(marks) FROM stud;
    ```
  * **Count Records:** Count students with marks greater than or equal to 80.
    ```sql
    mysql> SELECT COUNT(marks) FROM stud WHERE marks>=80;
    ```
  * **Sum of Marks:**
    ```sql
    mysql> SELECT SUM(marks) FROM stud;
    ```
  * **Average Marks:**
    ```sql
    mysql> SELECT AVG(marks) FROM stud;
    ```
  * **Next Step:** The practical could be extended by adding **constraints** (e.g., `PRIMARY KEY` on `rno`), creating a **VIEW** (e.g., of students with marks $> 80$), or creating an **INDEX** on the `name` column.

Would you like to continue the practical by adding a **Primary Key constraint** to the `stud` table?
