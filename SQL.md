# DDL || DML || DQL || TCL || DCL
| ID | Name  | Role      | Salary |
|----|-------|-----------|--------|
| 1  | John  | Manager   | 60000  |
| 2  | Jane  | Engineer  | 50000  |
| 3  | Jake  | Engineer  | 50000  |

Now, let's delve into the different types of SQL commands:

1. **DDL (Data Definition Language)**:
    - `CREATE`: Creates a new table.
        ```sql
        CREATE TABLE Employees (
            ID INT PRIMARY KEY,
            Name VARCHAR(50),
            Role VARCHAR(50),
            Salary INT
        );
        ```
    - `ALTER`: Modifies the table structure.
        ```sql
        ALTER TABLE Employees ADD COLUMN Department VARCHAR(50);
        ```
    - `DROP`: Deletes the table.
        ```sql
        DROP TABLE Employees;
        ```

2. **DML (Data Manipulation Language)**:
    - `SELECT`: Retrieves data from a table.
        ```sql
        SELECT * FROM Employees WHERE Role = 'Engineer';
        ```
    - `INSERT`: Adds new data into the table.
        ```sql
        INSERT INTO Employees (ID, Name, Role, Salary) VALUES (4, 'Mike', 'Intern', 30000);
        ```
    - `UPDATE`: Modifies existing data in the table.
        ```sql
        UPDATE Employees SET Salary = 55000 WHERE Name = 'Jane';
        ```
    - `DELETE`: Removes data from the table.
        ```sql
        DELETE FROM Employees WHERE Name = 'Jake';
        ```

3. **DCL (Data Control Language)**:
    - `GRANT`: Provides specific privileges to a user.
        ```sql
        GRANT SELECT, INSERT ON Employees TO some_user;
        ```
    - `REVOKE`: Removes specific privileges from a user.
        ```sql
        REVOKE INSERT ON Employees FROM some_user;
        ```

4. **TCL (Transaction Control Language)**:
    - `BEGIN TRANSACTION`: Begins a new transaction.
        ```sql
        BEGIN TRANSACTION;
        ```
    - `COMMIT`: Commits the current transaction.
        ```sql
        COMMIT;
        ```
    - `ROLLBACK`: Rolls back the current transaction to the beginning or to a savepoint.
        ```sql
        ROLLBACK;
        ```
    - `SAVEPOINT`: Creates a savepoint within a transaction to which you can later roll back.
        ```sql
        SAVEPOINT Savepoint1;
        ```
        example :
1. **COMMIT**:
    - What it does: It permanently saves any transactional updates into the database. After committing, you cannot undo the changes.
    
    - Example:
        ```sql
        BEGIN TRANSACTION; -- or just BEGIN;
        UPDATE Employees SET Salary = Salary + 5000 WHERE Role = 'Engineer';
        COMMIT;
        ```

2. **ROLLBACK**:
    - What it does: It undoes any changes made during the current transaction and reverts to the previous state before the transaction began.
    
    - Example:
        ```sql
        BEGIN TRANSACTION;
        DELETE FROM Employees WHERE Role = 'Intern';
        -- Oops, I changed my mind!
        ROLLBACK;
        ```

3. **SAVEPOINT**:
    - What it does: It creates a point within a transaction to which you can later roll back, instead of rolling back the entire transaction. This allows you to have nested levels of transactions.
    
    - Example:
        ```sql
        BEGIN TRANSACTION;
        UPDATE Employees SET Salary = 55000 WHERE Name = 'Jane';

        SAVEPOINT SavepointA;

        INSERT INTO Employees (Name, Role, Salary) VALUES ('Mike', 'Intern', 30000);

        -- Oh no, I shouldn't have added Mike as an Intern.
        ROLLBACK TO SavepointA; -- This will only undo the INSERT operation, not the UPDATE operation.

        COMMIT; -- This will save the changes from the UPDATE operation but not the INSERT.
        ```

5. **DQL (Data Query Language)**:
    - Primarily consists of the `SELECT` command to query and retrieve data. It's often considered a part of DML, but some sources separate it.
        ```sql
        SELECT Name, Role FROM Employees WHERE Salary > 50000;
        ```

The above examples provide an overview of the various SQL command types and how they operate on data and database structures.

# ACID Properties

The ACID properties are a set of properties that ensure reliable processing of transactions in a database management system (DBMS). The acronym "ACID" stands for Atomicity, Consistency, Isolation, and Durability.

1. **Atomicity**:
    - **Definition**: Atomicity ensures that a transaction is treated as a single unit, which means either all of its operations are executed or none of them are.
    - **Example**: Let's say you're making an online transfer from one bank account to another. The operation consists of deducting the amount from one account and adding it to another. If, for some reason, the amount is deducted from one account but not added to the receiving account (e.g., due to a system crash or failure), the whole transaction will be rolled back, ensuring that the amount is not lost.

2. **Consistency**:
    - **Definition**: Consistency ensures that the database remains in a consistent state before and after the transaction. This means that any transaction will bring the database from one valid state to another.
    - **Example**: Suppose there's a rule that the minimum balance in a bank account must be $100. If a transaction attempts to reduce the balance below $100, the transaction will be aborted to ensure the consistency rule is not violated.

3. **Isolation**:
    - **Definition**: Isolation ensures that concurrent execution of transactions results in a system state that would be obtained if transactions were executed serially (one after the other). This means that the operations of one transaction are isolated from the operations of other transactions.
    - **Example**: Imagine two people trying to book the last seat on a flight at the same time. Even if their booking operations happen concurrently, the isolation property will ensure that only one person successfully books the seat while the other receives an error or a notification that the seat has already been booked.

4. **Durability**:
    - **Definition**: Durability ensures that once a transaction has been committed, it remains committed even in the case of a system failure. This is typically achieved by storing the transaction logs or by ensuring data is flushed to permanent storage.
    - **Example**: After confirming the receipt of a payment in an online store, the transaction data is stored in permanent storage. If there's a system crash shortly after the payment confirmation, the data related to that transaction won't be lost, thanks to durability. When the system restarts, the transaction will still be in a committed state.

# Normalization

Normalization is a process in relational database design that organizes tables to minimize data redundancy and dependency by dividing larger tables into smaller ones and defining relationships between them. The main goals of normalization are:

1. Eliminating redundant data.
2. Ensuring data is stored logically.
3. Reducing the potential for anomalies during data operations (insertion, update, deletion).

**Real-time Example of Normalization**:

Imagine a university database with a table called `Students`:

| StudentID | FullName | Subjects                           | ContactNumber |
|-----------|----------|------------------------------------|---------------|
| 1         | John Doe | Math, Science, History             | 1234567890    |
| 2         | Jane Doe | Science, History                   | 0987654321    |
| 3         | Sam Smith| Math, History, Physical Education  | 1122334455    |

Issues with the table:

1. The Subjects column has multiple values, making it challenging to query specific subjects or modify one subject for a student.
2. If we need to change the name of a subject, we have to do it in multiple places.
3. Deleting a student row might inadvertently delete information about which subjects are offered.

To normalize, we'd break this table down:

1. **Student Table**:

| StudentID | FullName   | ContactNumber |
|-----------|------------|---------------|
| 1         | John Doe   | 1234567890    |
| 2         | Jane Doe   | 0987654321    |
| 3         | Sam Smith  | 1122334455    |

2. **Subjects Table**:

| SubjectID | SubjectName |
|-----------|-------------|
| 1         | Math        |
| 2         | Science     |
| 3         | History     |
| 4         | Physical Education |

3. **StudentSubjects Table**:

| StudentID | SubjectID |
|-----------|-----------|
| 1         | 1         |
| 1         | 2         |
| 1         | 3         |
| 2         | 2         |
| 2         | 3         |
| 3         | 1         |
| 3         | 3         |
| 3         | 4         |

This normalized design eliminates redundancy and reduces the potential for anomalies.

**Types of Normal Forms**:

1. **First Normal Form (1NF)**: Each table has a primary key, and each column contains atomic, indivisible values.
2. **Second Normal Form (2NF)**: All non-key attributes are fully functionally dependent on the primary key. This basically means no partial dependencies of columns on the primary key.
3. **Third Normal Form (3NF)**: All the attributes in a table are functionally dependent only on the primary key.
4. **Boyce-Codd Normal Form (BCNF)**: A more stringent version of the 3NF. For any non-trivial functional dependency X -> Y, X should be a super key.
5. **Fourth Normal Form (4NF)**: Concerned with multi-valued facts. There shouldn't be any dependencies amongst unrelated facts.
6. **Fifth Normal Form (5NF)**: Concerned with join dependencies.
7. **Sixth Normal Form (6NF)**: Concerned with temporal databases and how data is valid over certain periods of time.


# Keys
### 1. **Primary Key**:

- **Definition**: A column or set of columns that uniquely identifies a record within a table.
  
- **Use**: Ensures that each row in the table is unique.

- **Example**:
  ```
  CREATE TABLE Students (
      StudentID INT PRIMARY KEY,
      FirstName VARCHAR(255),
      LastName VARCHAR(255)
  );
  ```
  Here, `StudentID` is a primary key, meaning each student must have a unique ID.

### 2. **Foreign Key**:

- **Definition**: A column or set of columns in one table that refers to the primary key in another table.
  
- **Use**: Ensures referential integrity in the relationship between two tables.

- **Example**:
  ```
  CREATE TABLE Enrollments (
      EnrollmentID INT PRIMARY KEY,
      StudentID INT FOREIGN KEY REFERENCES Students(StudentID),
      CourseName VARCHAR(255)
  );
  ```
  Here, `StudentID` in the `Enrollments` table is a foreign key that references `StudentID` in the `Students` table.

### 3. **Unique Key**:

- **Definition**: A column or set of columns where all values must be unique, similar to the primary key, but a table can have multiple unique keys.
  
- **Use**: Ensures uniqueness of values in columns where it's applied.

- **Example**:
  ```
  CREATE TABLE Users (
      UserID INT PRIMARY KEY,
      Email VARCHAR(255) UNIQUE,
      Password VARCHAR(255)
  );
  ```
  Here, the `Email` column is a unique key, ensuring no two users have the same email address.

### 4. **Composite Key**:

- **Definition**: A type of key that consists of two or more columns to ensure uniqueness within the database.
  
- **Use**: When no single column is sufficient to uniquely identify records.

- **Example**:
  ```
  CREATE TABLE Enrollments (
      StudentID INT,
      CourseID INT,
      EnrollmentDate DATE,
      PRIMARY KEY (StudentID, CourseID)
  );
  ```
  Here, the combination of `StudentID` and `CourseID` acts as a composite key.

### 5. **Candidate Key**:

- **Definition**: A column or set of columns that can be chosen as a primary key. There can be multiple candidate keys, but only one can be the primary key.
  
- **Use**: To identify potential primary keys.

- **Example**: In a table with columns `Email`, `MobileNumber`, and `UserID`, all three columns can be candidate keys if they can uniquely identify a record.

### 6. **Secondary (or Alternate) Key**:

- **Definition**: Any candidate key which is not chosen as the primary key.
  
- **Use**: Useful for retrieval and access purposes.

- **Example**: If in a table `UserID` is the primary key, then `Email` and `MobileNumber` (both unique) would be secondary or alternate keys.

### 7. **Super Key**:

- **Definition**: A set of one or more columns that can be used to identify records uniquely. A super key may contain additional columns that are not strictly required for unique identification.
  
- **Use**: To understand potential combinations for unique identification.

- **Example**: In a table with columns `UserID` and `Email`, `{UserID}`, `{Email}`, and `{UserID, Email}` are all super keys, but only the first two are candidate keys.

# `DROP` vs  `DELETE` vs `TRUNCATE`

### 1. `DELETE`:

- **Definition**: `DELETE` is used to remove rows from a table based on a condition. If no condition is specified, all rows will be deleted.
  
- **Characteristics**:
  - It's a logged operation, meaning every row deletion is recorded in the logs. This can make the operation slower, especially for large data.
  - It doesn't free the space associated with the table but makes it available for future inserts.
  - You can use a `WHERE` clause to specify criteria for deletion.
  - It triggers DELETE triggers in the database.

- **Example**:
  ```sql
  DELETE FROM students WHERE student_id = 5;
  ```

### 2. `TRUNCATE`:

- **Definition**: `TRUNCATE` quickly removes all rows from a table, resetting the space occupied by the table to its minimum.
  
- **Characteristics**:
  - Typically, it's a minimally logged operation, making it faster than DELETE.
  - It frees the space back to the system, effectively resetting the table to be like a new one.
  - You cannot use a `WHERE` clause. It will remove all rows.
  - Doesn't generally activate triggers as it doesn't operate on individual rows.

- **Example**:
  ```sql
  TRUNCATE TABLE students;
  ```

### 3. `DROP`:

- **Definition**: The `DROP` command removes an entire table or database from the database system.
  
- **Characteristics**:
  - All space associated with the object (table, database, etc.) is released back to the system.
  - The structure/schema of the object is also deleted, meaning you lose both the data and the design.
  - It's not a logged operation in terms of individual rows (since the whole structure is removed).
  - There's no going back after a DROP without a backup.

- **Example**:
  ```sql
  DROP TABLE students;
  ```

### Main Differences:

- **Scope**: `DELETE` operates on rows, `TRUNCATE` operates on the entire table (but retains the structure), and `DROP` removes the entire table or database structure and data.
- **Speed**: `TRUNCATE` is usually faster than `DELETE` because it's less logged. `DROP` is fast because it removes the entire object.
- **Space**: After `TRUNCATE` and `DROP`, space is freed to the system, while `DELETE` just makes it available for future rows in the same table.
- **Flexibility**: Only `DELETE` allows for conditional removal based on the data in the rows.

# Join 

### 1. **INNER JOIN (or JOIN)**:

- **Definition**: Returns records that have matching values in both tables.
  
- **Example**:
  ```sql
  SELECT employees.name, orders.order_id
  FROM employees
  INNER JOIN orders ON employees.employee_id = orders.employee_id;
  ```
  This returns all employees and their orders, but only for employees who have made at least one order.

### 2. **LEFT JOIN (or LEFT OUTER JOIN)**:

- **Definition**: Returns all records from the left table, and the matched records from the right table. If there's no match, the result is NULL on the right side.
  
- **Example**:
  ```sql
  SELECT students.name, courses.course_name
  FROM students
  LEFT JOIN enrollments ON students.student_id = enrollments.student_id
  LEFT JOIN courses ON enrollments.course_id = courses.course_id;
  ```
  This fetches all students and the courses they are enrolled in, but it will also include students not enrolled in any course (with NULL for course names).

### 3. **RIGHT JOIN (or RIGHT OUTER JOIN)**:

- **Definition**: Returns all records from the right table, and the matched records from the left table. If there's no match, the result is NULL on the left side.
  
- **Example**:
  ```sql
  SELECT students.name, books.book_title
  FROM students
  RIGHT JOIN book_ownership ON students.student_id = book_ownership.student_id
  RIGHT JOIN books ON book_ownership.book_id = books.book_id;
  ```
  This fetches all books and their respective owners. If a book has no owner, it'll still be listed (with NULL for the student's name).

### 4. **FULL JOIN (or FULL OUTER JOIN)**:

- **Definition**: Returns all records when there's a match in one of the left or right tables. Combines the effects of both LEFT and RIGHT joins.
  
- **Example**:
  ```sql
  SELECT customers.name, orders.order_id
  FROM customers
  FULL JOIN orders ON customers.customer_id = orders.customer_id;
  ```
  This fetches all customers and their orders, but it also includes customers with no orders and orders that have no linked customer.

### 5. **CROSS JOIN**:

- **Definition**: Returns the Cartesian product of the two tables. It pairs every row from the first table with every row from the second table.
  
- **Example**:
  ```sql
  SELECT colors.color_name, sizes.size_label
  FROM colors
  CROSS JOIN sizes;
  ```
  If you have a `colors` table with colors (Red, Blue) and a `sizes` table with sizes (Small, Medium), this would return all combinations: Red-Small, Red-Medium, Blue-Small, Blue-Medium.

### 6. **SELF JOIN**:

- **Definition**: A join of a table with itself. Useful when the data related to each other is in the same table.
  
- **Example**:
  ```sql
  SELECT A.employee_name, B.employee_name as 'Manager'
  FROM employees A, employees B
  WHERE A.manager_id = B.employee_id;
  ```
  This fetches every employee alongside their respective managers from an `employees` table, where managers are also employees in the same table.

  # SQL-Practice


INSERT

-- Example: 
INSERT INTO Student.student_express(firstname ,lastname,email) VALUES 	('jiya','pal' 'jiya@gmail.com');

INSERT MULTIPLE  
Example: 
INSERT INTO Student.student_express(firstname ,lastname,email) VALUES 	('jiya','pal','jiya@gmail.com'),
									('tiya','tiwari','tiya@gmail.com'),
								        ('maya','tejwani','maya@gmail.com');


UPDATE : The UPDATE statement is used to modify the existing records in a table. 

-- Note: Be careful when updating records in a table! Notice the WHERE clause in the UPDATE statement. 
-- The WHERE clause specifies which record(s) that should be updated. 
-- If you omit the WHERE clause, all records in the table will be updated!


-- Example: 
Update Student.student_express set firstname ="sejal"  where id =1;


DELETE :The DELETE statement is used to delete existing records in a table.
 -- Note: Be careful when deleting records in a table! Notice the WHERE clause in the DELETE statement.
-- The WHERE clause specifies which record(s) should be deleted. 
-- If you omit the WHERE clause, all records in the table will be deleted!


for delete all : delete table table_name;

syntex : DELETE FROM table_name WHERE condition;

Example : delete from Student.student_express  where id=3003;

SELECT : The SELECT statement is used to select data from a database.
-- The data returned is stored in a result table, called the result-set.
Syntex : select * from table_name;
SELECT * FROM Student.student_express;
SELECT * FROM Student.student_express where firstname= "sejal";

Where Caluse Operator:
Operator	Description	
=		Equal	
>		Greater than	
<		Less than	
>=		Greater than or equal	
<=		Less than or equal	
<>		Not equal. Note: In some versions of SQL this operator may be written as !=	
BETWEEN		Between a certain range	
LIKE		Search for a pattern	
IN		To specify multiple possible values for a column


ORDER BY  : MySQL order by data sorting is important where we want to display the data in any particular order.
MySQL provides ORDER BY clause to display data in an ordered way.
The result set can be sorted in either ascending or descending order, by default it sort the data in ascending order and we
can also sort by either single or multiple columns.
Syntax : SELECT * FROM  table_name ORDER BY column_name asc or desc;
Example : 
select  * from Student.student_express order by id desc , firstname desc, lastname asc , email asc; 

LIMIT : LIMIT clause to select a limited number of records
Syntax :
SELECT column_name(s)
FROM table_name
WHERE condition
LIMIT number[starting position] ,number [number  of rows to skip];

Example : 
-- SELECT LAST 3 ID FORM TABLE
select * from Student.Student_Master where Student_Master.Stu_id order by Stu_id DESC LIMIT  0,3;

IN :The IN operator allows you to specify multiple values in a WHERE clause.
The IN operator is a shorthand for multiple OR conditions.

-- select  student  name where id = 10,100 ?
SELECT * FROM Student.Student_Master where Student_Master.Stu_id  IN ('10','100'); 

NOT IN : reverse  of IN Operator 

AND OR NOT : 
The WHERE clause can be combined with AND, OR, and NOT operators.
The AND and OR operators are used to filter records based on more than one condition:
The AND operator displays a record if all the conditions separated by AND are TRUE. 
syntax : 
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;

Example : 
The OR operator displays a record if any of the conditions separated by OR is TRUE. 
syntax : 
SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2 OR condition3 ...;
Example : 

The NOT operator displays a record if the condition(s) is NOT TRUE.
Syntax : 
SELECT column1
FROM table_name
WHERE NOT condition1;
Example : 



LIKE : 
The LIKE operator is used in a WHERE clause to search for a specified pattern in a column.

There are two wildcards often used in conjunction with the LIKE operator:
  We can use and , or with like operator.
 The percent sign (%) represents zero, one, or multiple characters
 The underscore sign (_) represents one, single character

Syntax : 
SELECT column1, column2, ...
FROM table_name
WHERE columnN LIKE pattern;

Example : 
SELECT * FROM Student.student_express;

select  * from Student.student_express  where  firstname like 'a%';-- Finds any values that start with "a"
select  * from Student.student_express  where  firstname like '%a' and lastname like '%a';-- 	Finds any values that end with "a" in any position
select  * from Student.student_express  where  firstname like '_r%' and lastname like '_r%';-- 	Finds any values that have "r" in the second position
select  * from Student.student_express  where  firstname like 'a__%' and lastname like 'a__%';-- 	Finds any values that start with "a" and are at least 2 characters in length
select  * from Student.student_express  where  firstname  like 'a___%' and lastname like 'a___%';-- 	Finds any values that start with "a" and are at least 3 characters in length
select  * from Student.student_express  where  firstname like '   a%a';-- 	Finds any values that start with "a" and ends with "o" -- like cannot accepct space 


ANY  :
ALL :
BETWEEN :
JOIN : A JOIN clause is used to combine rows from two or more tables, based on a related column between them.

INNER JOIN : 
SELECT * FROM candidate.candidate_master as cm join 
candidate.candidate_academic_info as cai on 
cm.candidate_id = cai.candidate_id; 

> LEFT JOIN 
SELECT * FROM candidate.candidate_master as cm LEFT JOIN
candidate.candidate_academic_info as cai on 
cm.candidate_id = cai.candidate_id;

> RIGHT JOIN
SELECT * FROM candidate.candidate_master as cm RIGHT JOIN
candidate.candidate_academic_info as cai on 
cm.candidate_id = cai.candidate_id;


> CROSS JOIN
SELECT * FROM candidate.candidate_master as cm  CROSS JOIN 
candidate.candidate_academic_info as cai on 
cm.candidate_id = cai.candidate_id;

> SELF JOIN 


_______________
# SQL-Practice
Aggregate functions ?
SQL aggregation function is used to perform the calculations on multiple rows of a single column of a table. It returns a single value.

![image](https://user-images.githubusercontent.com/127746039/229786223-d536c148-b30a-4f7b-aace-f0d507508b83.png)

The GROUP BY

The GROUP BY statement groups rows that have the same values into summary rows, like "find the number of customers in each country".
The GROUP BY statement is often used with aggregate functions (COUNT(), MAX(), MIN(), SUM(), AVG()) to group the result-set by one or more columns.

Syntax :
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
ORDER BY column_name(s);



The HAVING 

The HAVING clause was added to SQL because the WHERE keyword cannot be used with aggregate functions.

Syntax : 
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
HAVING condition
ORDER BY column_name(s); 



-- RANDOM ID GENRATOR 
select * from Student.Student_Master where Student_Master.Stu_id order by rand() LIMIT 1;

-- check any number is in 
SELECT 25 IN(15,10,25);

--Multiplay two columns in SQL 
SELECT id , cost*quantity as  TOTAL  FROM new_schema.try  ;

https://www.hackerrank.com/challenges/weather-observation-station-5/problem?isFullScreen=true&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen



