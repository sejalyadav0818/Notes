
---

# SQL Interview Questions :

Structured Query Language (SQL) is a domain-specific language used in programming and managing relational databases. Proficiency in SQL is crucial for roles like database administrators, data analysts, and backend developers. This README provides an overview of commonly asked SQL interview questions with examples.

## Questions & Answers

### 1. **What is SQL?**
   - **Answer**: SQL stands for Structured Query Language. It's a standard language designed for managing data in relational database management systems (RDBMS).
   - **Example**: 
     ```sql
     SELECT first_name, last_name FROM employees;
     ```

### 2. **Distinguish between `INNER JOIN` and `LEFT JOIN`.**
   - **Answer**: An `INNER JOIN` returns rows from both tables that satisfy the condition. `LEFT JOIN` (or `LEFT OUTER JOIN`) returns all rows from the left table and matching rows from the right table. If no match is found, the result is `NULL`.
   - **Example**:
     ```sql
     -- INNER JOIN
     SELECT orders.id, customers.name 
     FROM orders 
     INNER JOIN customers ON orders.customer_id = customers.id;

     -- LEFT JOIN
     SELECT students.name, courses.course_name 
     FROM students 
     LEFT JOIN course_enrollments ON students.id = course_enrollments.student_id;
     ```

### 3. **What is a primary key?**
   - **Answer**: A primary key is a unique identifier for a record in a database table. It must contain unique values and cannot be `NULL`.
   - **Example**: In an `employees` table, an `employee_id` column could serve as a primary key.

### 4. **Describe the `GROUP BY` clause in SQL.**
   - **Answer**: `GROUP BY` groups rows that have the same values in specified columns into summary rows. It's often used with aggregate functions like `COUNT`, `MAX`, `MIN`, `SUM`, and `AVG`.
   - **Example**:
     ```sql
     SELECT department, COUNT(employee_id) 
     FROM employees 
     GROUP BY department;
     ```

### 5. **Explain the difference between `HAVING` and `WHERE` clause.**
   - **Answer**: Both clauses are used to filter the result set. `WHERE` is used to filter rows before they are grouped, while `HAVING` is used to filter aggregated data or the result of aggregate functions.
   - **Example**:
     ```sql
     SELECT department, COUNT(employee_id) as num_employees 
     FROM employees 
     WHERE department != 'HR' 
     GROUP BY department 
     HAVING num_employees > 10;
     ```

### 6. **What is a stored procedure?**
   - **Answer**: A stored procedure is a prepared SQL code that can be saved and reused. In other words, it's a reusable function written in SQL.
   - **Example**:
     ```sql
     CREATE PROCEDURE SelectAllEmployees
     AS
     SELECT * FROM employees;
     GO;
     ```

### 7. **Explain the `UNION` operation in SQL.**
   - **Answer**: `UNION` is used to combine the result sets of two or more `SELECT` statements. It removes duplicate rows between the various `SELECT` statements.
   - **Example**:
     ```sql
     SELECT city FROM customers
     UNION
     SELECT city FROM suppliers
     ORDER BY city;
     ```

### 8. **What are indexes and why are they important in SQL databases?**
   - **Answer**: An index is a database object that enhances the speed of data retrieval operations. It provides quicker access to rows by creating pointers to the data.
   - **Example**:
     ```sql
     CREATE INDEX idx_employee_name
     ON employees (first_name, last_name);
     ```

### 9. **What is a subquery, and what are its types?**
   - **Answer**: A subquery is a query nested inside another query. It can return data that will be used in the main query to further restrict the results. Subqueries can be classified as correlated and non-correlated.
   - **Example**:
     ```sql
     SELECT first_name 
     FROM employees 
     WHERE department_id = (SELECT id FROM departments WHERE name = 'Finance');
     ```

### 10. **Explain the concept of `NORMALIZATION`.**
   - **Answer**: Normalization is a systematic approach to decompose tables to eliminate data redundancy and undesirable characteristics like insertion, update, and delete anomalies.
   - **Example**: Consider a table storing user details and their orders. To normalize, we could separate the data into two tables: one for user details and another for orders. This way, we won't have to repeat user details for each order entry.

---

