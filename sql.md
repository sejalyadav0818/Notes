1. **What is SQL?**
   - **Answer:** SQL (Structured Query Language) is a domain-specific language used for managing and manipulating relational databases.

2. **Explain the difference between `DELETE` and `TRUNCATE` commands.**
   - **Answer:** `DELETE` removes rows from a table based on a condition, while `TRUNCATE` removes all rows from a table without any conditions.

     ```sql
     -- DELETE
     DELETE FROM employees WHERE department_id = 3;

     -- TRUNCATE
     TRUNCATE TABLE employees;
     ```

3. **What is the purpose of the `INNER JOIN` clause?**
   - **Answer:** `INNER JOIN` is used to combine rows from two or more tables based on a related column.

     ```sql
     SELECT orders.order_id, customers.customer_name
     FROM orders
     INNER JOIN customers ON orders.customer_id = customers.customer_id;
     ```

4. **Explain the concept of normalization in databases.**
   - **Answer:** Normalization is the process of organizing data to minimize redundancy and dependency by dividing large tables into smaller related tables.

     ```sql
     -- Example Normalized Tables
     CREATE TABLE authors (
       author_id INT PRIMARY KEY,
       author_name VARCHAR(50)
     );

     CREATE TABLE books (
       book_id INT PRIMARY KEY,
       title VARCHAR(100),
       author_id INT,
       FOREIGN KEY (author_id) REFERENCES authors(author_id)
     );
     ```

5. **What is an index, and why is it important?**
   - **Answer:** An index is a data structure that improves the speed of data retrieval operations on a database table. It allows for faster lookup of rows based on indexed columns.

     ```sql
     -- Example Indexing
     CREATE INDEX idx_last_name ON employees(last_name);
     ```

6. **Explain the purpose of the `GROUP BY` clause.**
   - **Answer:** `GROUP BY` is used to arrange identical data into groups based on specified columns, often used with aggregate functions.

     ```sql
     SELECT department, AVG(salary) AS avg_salary
     FROM employees
     GROUP BY department;
     ```

7. **What is a subquery, and how is it different from a join?**
   - **Answer:** A subquery is a query nested within another query. It can be used in various parts of a SQL statement. A join is used to combine rows from two or more tables based on a related column.

     ```sql
     -- Subquery
     SELECT product_name
     FROM products
     WHERE category_id IN (SELECT category_id FROM categories WHERE category_name = 'Electronics');
     ```

8. **Explain the purpose of the `HAVING` clause.**
   - **Answer:** The `HAVING` clause is used in conjunction with `GROUP BY` to filter the results of aggregate functions based on specified conditions.

     ```sql
     SELECT department, AVG(salary) as avg_salary
     FROM employees
     GROUP BY department
     HAVING avg_salary > 50000;
     ```

9. **What is the difference between `UNION` and `UNION ALL`?**
   - **Answer:** `UNION` combines the results of two or more SELECT statements, removing duplicates, while `UNION ALL` includes all rows, including duplicates.

     ```sql
     SELECT product_id, product_name FROM electronics
     UNION
     SELECT product_id, product_name FROM appliances;
     ```

10. **Explain the concept of a stored procedure.**
    - **Answer:** A stored procedure is a set of SQL statements that can be saved and reused. It can accept parameters and be called with those parameters.

     ```sql
     DELIMITER //

     CREATE PROCEDURE GetEmployeeCount(IN department_id INT)
     BEGIN
       SELECT COUNT(*) FROM employees WHERE department_id = department_id;
     END //

     DELIMITER ;

     -- Call the stored procedure
     CALL GetEmployeeCount(3);
     ```

11. **What is the purpose of the `CASE` statement?**
    - **Answer:** The `CASE` statement is used to perform conditional logic in SQL queries, allowing for the execution of different code based on specified conditions.

     ```sql
     SELECT product_name,
            CASE
              WHEN price > 1000 THEN 'Expensive'
              WHEN price > 500 THEN 'Moderate'
              ELSE 'Affordable'
            END AS price_category
     FROM products;
     ```

12. **Explain the difference between `UNIQUE` and `PRIMARY KEY` constraints.**
    - **Answer:** Both ensure unique values, but a table can have multiple `UNIQUE` constraints, whereas it can have only one `PRIMARY KEY` constraint.

     ```sql
     -- UNIQUE constraint
     CREATE TABLE users (
       username VARCHAR(20) UNIQUE,
       email VARCHAR(50) UNIQUE
     );

     -- PRIMARY KEY constraint
     CREATE TABLE products (
       product_id INT PRIMARY KEY,
       product_name VARCHAR(50)
     );
     ```

13. **What is the purpose of the `ORDER BY` clause in SQL?**
    - **Answer:** `ORDER BY` is used to sort the result set of a query based on one or more columns, either in ascending or descending order.

     ```sql
     SELECT product_name, price
     FROM products
     ORDER BY price DESC;
     ```

14. **Explain the concept of a self-join.**
    - **Answer:** A self-join is a regular join, but the table is joined with itself. It is often used when a table contains hierarchical data.

     ```sql
     -- Example Self-Join
     CREATE TABLE employees (
       employee_id INT PRIMARY KEY,
       employee_name VARCHAR(50),
       manager_id INT
     );

     SELECT e1.employee_name AS employee, e2.employee_name AS manager
     FROM employees e1
     JOIN employees e2 ON e1.manager_id = e2.employee_id;
     ```

15. **What is the purpose of the `LIKE` operator in SQL?**
    - **Answer:** The `LIKE` operator is used to search for a specified pattern in a column. It can include wildcard characters such as `%` and `_`.

     ```sql
     SELECT product_name
     FROM products
     WHERE product_name LIKE 'App%';
     ```

16. **Explain the purpose of the `IN` operator.**
    - **Answer:** The `IN` operator is used to filter results based on a list of specified values.

     ```sql
     SELECT product_name
     FROM products
     WHERE category_id IN (1, 3, 5);
     ```

17. **What is the purpose of the `COUNT` aggregate function?**
    - **Answer:** The `COUNT` function is used to count the number of rows that meet

 a specified condition.

     ```sql
     SELECT department, COUNT(*) AS employee_count
     FROM employees
     GROUP BY department;
     ```

18. **Explain the concept of database transactions and the `COMMIT` statement.**
    - **Answer:** A transaction is a sequence of one or more SQL statements that are executed as a single unit of work. The `COMMIT` statement is used to save the changes made during the transaction.

     ```sql
     -- Example Transaction
     START TRANSACTION;
     UPDATE accounts SET balance = balance - 100 WHERE account_id = 123;
     UPDATE accounts SET balance = balance + 100 WHERE account_id = 456;
     COMMIT;
     ```

19. **What is the purpose of the `MAX` aggregate function?**
    - **Answer:** The `MAX` function is used to find the highest value in a column.

     ```sql
     SELECT department, MAX(salary) AS max_salary
     FROM employees
     GROUP BY department;
     ```

20. **Explain the concept of a view in SQL.**
    - **Answer:** A view is a virtual table based on the result of a SELECT query. It is used to simplify complex queries and can be referenced like a table.

     ```sql
     CREATE VIEW high_salary_employees AS
     SELECT employee_id, employee_name
     FROM employees
     WHERE salary > 75000;

     SELECT * FROM high_salary_employees;
     ```

21. **Explain the purpose of the `BETWEEN` operator.**
    - **Answer:** The `BETWEEN` operator is used to filter results within a specified range.

     ```sql
     SELECT product_name, price
     FROM products
     WHERE price BETWEEN 50 AND 100;
     ```

22. **What is the purpose of the `IS NULL` operator?**
    - **Answer:** The `IS NULL` operator is used to filter results where a column contains NULL values.

     ```sql
     SELECT customer_name
     FROM customers
     WHERE phone_number IS NULL;
     ```

23. **Explain the concept of a foreign key.**
    - **Answer:** A foreign key is a column or a set of columns in a table that refers to the primary key of another table. It establishes a link between the two tables.

     ```sql
     -- Example Foreign Key
     CREATE TABLE orders (
       order_id INT PRIMARY KEY,
       customer_id INT,
       FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
     );
     ```

24. **What is the purpose of the `SUM` aggregate function?**
    - **Answer:** The `SUM` function is used to calculate the sum of values in a numeric column.

     ```sql
     SELECT department, SUM(salary) AS total_salary
     FROM employees
     GROUP BY department;
     ```

25. **Explain the concept of an SQL injection and how to prevent it.**
    - **Answer:** SQL injection is a type of attack where malicious SQL statements are inserted into user input fields. To prevent it, use parameterized queries or prepared statements.

     ```sql
     -- Example Parameterized Query (in PHP)
     $sql = "SELECT * FROM users WHERE username = ? AND password = ?";
     $stmt = $conn->prepare($sql);
     $stmt->bind_param("ss", $username, $password);
     $stmt->execute();
     ```

26. **What is the purpose of the `DISTINCT` keyword?**
    - **Answer:** The `DISTINCT` keyword is used to retrieve unique values from a specified column.

     ```sql
     SELECT DISTINCT department
     FROM employees;
     ```

27. **Explain the difference between a primary key and a unique key.**
    - **Answer:** Both ensure uniqueness, but a table can have only one primary key, which also implies it cannot have NULL values. Multiple unique keys can exist in a table.

     ```sql
     -- Primary Key
     CREATE TABLE students (
       student_id INT PRIMARY KEY,
       student_name VARCHAR(50)
     );

     -- Unique Key
     CREATE TABLE products (
       product_id INT,
       product_name VARCHAR(50),
       UNIQUE (product_id)
     );
     ```

28. **What is the purpose of the `LIMIT` clause in SQL?**
    - **Answer:** The `LIMIT` clause is used to restrict the number of rows returned by a query.

     ```sql
     SELECT product_name
     FROM products
     LIMIT 10;
     ```

29. **Explain the concept of an aggregate function.**
    - **Answer:** Aggregate functions perform a calculation on a set of values and return a single value. Examples include `SUM`, `AVG`, `COUNT`, and `MAX`.

     ```sql
     SELECT department, AVG(salary) AS avg_salary
     FROM employees
     GROUP BY department;
     ```

30. **What is the purpose of the `HAVING` clause?**
    - **Answer:** The `HAVING` clause filters the results of aggregate functions based on specified conditions, similar to the `WHERE` clause for individual rows.

     ```sql
     SELECT department, AVG(salary) as avg_salary
     FROM employees
     GROUP BY department
     HAVING avg_salary > 50000;
     ```

31. **Explain the purpose of the `CASE` statement in a WHERE clause.**
    - **Answer:** The `CASE` statement in a WHERE clause is used for conditional filtering based on specified conditions.

     ```sql
     SELECT product_name, price
     FROM products
     WHERE
       CASE
         WHEN category_id = 1 THEN price > 50
         WHEN category_id = 2 THEN price > 100
         ELSE price > 20
       END;
     ```

32. **What is the purpose of the `UNIQUE` constraint?**
    - **Answer:** The `UNIQUE` constraint ensures that all values in a column are unique. It is often used for columns that should not contain duplicate values.

     ```sql
     CREATE TABLE employees (
       employee_id INT PRIMARY KEY,
       email VARCHAR(50) UNIQUE,
       -- Other columns...
     );
     ```

33. **Explain the concept of a self-contained subquery.**
    - **Answer:** A self-contained subquery is independent and does not rely on the outer query. It can be executed independently of the outer query.

     ```sql
     SELECT product_name
     FROM products
     WHERE price > (SELECT AVG(price) FROM products);
     ```

34. **What is the purpose of the `AS` keyword in SQL?**
    - **Answer:** The `AS` keyword is used to alias column names or table names, providing a temporary name for better readability.

     ```sql
     SELECT product_name AS "Product Name", price AS "Unit Price"
     FROM products;
     ```

35. **Explain the difference between a clustered and a non-clustered index.**
    - **Answer:** A clustered index determines the physical order of data rows in a table, while a non-clustered index does not affect the physical order and is stored separately.

     ```sql
     -- Clustered Index
     CREATE CLUSTERED INDEX idx_order_date ON orders(order_date);

     -- Non-Clustered Index
     CREATE NONCLUSTERED INDEX idx_customer_id ON orders(customer_id);
     ```

36. **What is the purpose of the `EXISTS` operator?**
    - **Answer:** The `EXISTS` operator is used to test the existence of rows returned by a subquery. It returns true if the subquery returns any rows.

     ```sql
     SELECT product_name
     FROM products p
     WHERE EXISTS (SELECT 1 FROM order_items oi WHERE oi.product_id = p.product_id);
     ```

37. **Explain the concept of a recursive common table expression (CTE).**
    - **Answer:** A recursive CTE is used to perform recursive queries, often used for hierarchical data structures.

     ```sql
     WITH RECURSIVE EmployeeHierarchy AS (
       SELECT employee_id, manager_id
       FROM employees
       WHERE manager_id IS NULL
       UNION ALL
       SELECT e.employee_id, e.manager_id
       FROM employees e
       JOIN EmployeeHierarchy eh ON e.manager_id = eh.employee_id
     )
     SELECT * FROM EmployeeHierarchy;
     ```

38. **What is the purpose of the `COALESCE` function?**
    - **Answer:** The `COALESCE` function is used to return the first non-null expression among its arguments.

     ```sql
     SELECT product_name, COALESCE(discounted_price, regular_price) AS final_price
     FROM products;
     ```

39. **Explain the concept of an SQL view with an example.**
    - **Answer:** An SQL view is a virtual table based on the result of a SELECT query. It simplifies complex queries and can be referenced like a table.

     ```sql
     CREATE VIEW high_salary_employees AS
     SELECT employee_id, employee_name
     FROM employees
     WHERE salary > 75000;

     SELECT * FROM high_salary_employees;
     ```

40. **What is the purpose of the `TRANSACTION` statement?**
    - **Answer:** The `TRANSACTION` statement is used to start a new transaction manually, allowing a set of SQL statements to be treated as a single unit of work.

     ```sql
     -- Example Transaction
     START TRANSACTION;
     UPDATE accounts SET balance = balance - 100 WHERE account_id = 123;
     UPDATE accounts SET balance = balance + 100 WHERE account_id = 456;
     COMMIT;
     ```
