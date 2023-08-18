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

# `DROP` vs  `DELETE` vs `TRUNCATE

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


