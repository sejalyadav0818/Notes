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

5. **DQL (Data Query Language)**:
    - Primarily consists of the `SELECT` command to query and retrieve data. It's often considered a part of DML, but some sources separate it.
        ```sql
        SELECT Name, Role FROM Employees WHERE Salary > 50000;
        ```

The above examples provide an overview of the various SQL command types and how they operate on data and database structures.
