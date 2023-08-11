

# DBMS Interview Questions :

Database Management Systems (DBMS) play a pivotal role in software applications that rely on structured storage of data. Understanding core concepts of DBMS is essential for software developers, database administrators, and data architects. 

## Questions & Answers

### 1. **What is DBMS?**
   - **Answer**: A Database Management System (DBMS) is software that controls the storage, retrieval, and updating of data in a database.
   - **Example**: Oracle, MySQL, and PostgreSQL are popular RDBMS systems.

### 2. **Distinguish between a database and a DBMS.**
   - **Answer**: A database is a structured collection of data, whereas a DBMS is the software that manages and interacts with the database.
   - **Example**: Consider a library. The collection of books is similar to a database, while the system used to manage the check-in/check-out and arrangement of books is like a DBMS.

### 3. **What is normalization? Why is it important?**
   - **Answer**: Normalization is the process of organizing data in a database to reduce redundancy and prevent data anomalies. It ensures data integrity and optimizes storage.
   - **Example**: Without normalization, a database that stores an address for each transaction could have multiple different addresses for a single customer, leading to confusion and redundancy.

### 4. **Describe the different normal forms in normalization.**
   - **Answer**: There are several normal forms, including 1NF, 2NF, 3NF, BCNF, 4NF, etc. Each form has a set of specific rules or conditions that the database schema should satisfy.
   - **Example**: 
     - **1NF**: Each table has atomic (indivisible) columns.
     - **2NF**: No non-prime attribute is dependent on the proper subset of any candidate key.
     - **3NF**: Every non-prime attribute is functionally dependent on the primary key.

### 5. **What are the ACID properties in a database?**
   - **Answer**: ACID stands for Atomicity, Consistency, Isolation, and Durability. These properties ensure reliable processing of transactions within a database.
   - **Example**: In a banking system, if you are transferring money from one account to another, the operation needs to either fully complete (money is deducted from one account and added to another) or fully fail. Partial completion could lead to data inconsistencies.

### 6. **What is SQL?**
   - **Answer**: SQL (Structured Query Language) is a domain-specific language used for managing and querying data in a relational database.
   - **Example**: 
     ```sql
     SELECT first_name, last_name FROM users WHERE age > 21;
     ```

### 7. **Explain the difference between DDL and DML.**
   - **Answer**: DDL (Data Definition Language) deals with database schema and structure modifications (e.g., `CREATE`, `ALTER`, `DROP`). DML (Data Manipulation Language) deals with data manipulation and includes commands like `SELECT`, `INSERT`, `UPDATE`, and `DELETE`.
   - **Example**:
     - DDL: 
       ```sql
       CREATE TABLE employees (ID int, Name varchar(255));
       ```
     - DML:
       ```sql
       INSERT INTO employees (ID, Name) VALUES (1, 'John Doe');
       ```

### 8. **What is a primary key?**
   - **Answer**: A primary key is a unique identifier for a record in a table. It ensures each record can be uniquely distinguished.
   - **Example**: In a `users` table, `user_id` could be a primary key, ensuring each user has a unique identifier.

### 9. **Distinguish between primary key and foreign key.**
   - **Answer**: A primary key uniquely identifies a record within a table, while a foreign key in one table is the primary key of another table, establishing a link between them.
   - **Example**: In a relational database with `authors` and `books` tables, the `author_id` could be the primary key in the `authors` table and a foreign key in the `books` table.

### 10. **What is a deadlock? How can it be avoided?**
   - **Answer**: A deadlock is a situation in which two or more transactions are unable to proceed because each is waiting for the other to release a resource. Deadlocks can be prevented through techniques like timeout, deadlock detection, or ordering the resources.
   - **Example**: Transaction A holds Resource 1 and waits for Resource 2, which is held by Transaction B. Transaction B waits for Resource 1, resulting in a cyclic wait condition or deadlock.

### 11. **What is indexing and why is it used?**
   - **Answer**: Indexing is a technique used to speed up retrieval operations on a database. It works similarly to an index in a book, allowing the database system to find the required data without scanning every row in a database table.
   - **Example**: A `user_email` index on the `users` table ensures faster lookups when searching by email.

### 12. **What are views in a database?**
   - **Answer**: A view is a virtual table based on the result-set of an SQL statement. It contains rows and columns, similar to a real table, but does not store data physically.
   - **Example**: A view that lists all users who have registered in the past month can be created using an SQL statement filtering on the registration date.

### 13. **Describe the difference between inner join, left join, and right join in SQL.**
   - **Answer**: An inner join returns rows when there is a match in both tables. A left join returns all rows from the left table and matching rows from the right table. A right join returns all rows from the right table and matching rows from the left table.
   - **Example**:
     ```sql
     SELECT orders.order_id, customers.customer_name
     FROM orders
     INNER JOIN customers
     ON orders.customer_id = customers.customer_id;
     ```

---



