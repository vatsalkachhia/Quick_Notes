Here are some SQL interview questions that range from basic to advanced levels:

### Basic Level

1. **Select all columns and rows from a table**
   ```sql
   SELECT * FROM employees;
   ```

2. **Select specific columns from a table**
   ```sql
   SELECT first_name, last_name, department FROM employees;
   ```

3. **Select distinct values from a column**
   ```sql
   SELECT DISTINCT department FROM employees;
   ```

4. **Filter results using a WHERE clause**
   ```sql
   SELECT * FROM employees WHERE department = 'Sales';
   ```

5. **Use aggregate functions**
   ```sql
   SELECT COUNT(*) FROM employees;
   SELECT AVG(salary) FROM employees;
   SELECT MAX(salary) FROM employees;
   ```

### Intermediate Level

6. **Group results using GROUP BY**
   ```sql
   SELECT department, COUNT(*) FROM employees GROUP BY department;
   ```

7. **Filter groups using HAVING**
   ```sql
   SELECT department, COUNT(*) FROM employees GROUP BY department HAVING COUNT(*) > 10;
   ```

8. **Join two tables**
   ```sql
   SELECT e.first_name, e.last_name, d.department_name 
   FROM employees e
   JOIN departments d ON e.department_id = d.department_id;
   ```

9. **Use subqueries**
   ```sql
   SELECT first_name, last_name 
   FROM employees 
   WHERE salary > (SELECT AVG(salary) FROM employees);
   ```

10. **Order results**
    ```sql
    SELECT * FROM employees ORDER BY last_name ASC;
    SELECT * FROM employees ORDER BY salary DESC;
    ```

### Advanced Level

11. **Use window functions**
    ```sql
    SELECT first_name, last_name, salary, 
           RANK() OVER (ORDER BY salary DESC) AS salary_rank 
    FROM employees;
    ```

12. **Perform a self-join**
    ```sql
    SELECT e1.first_name AS Employee, e2.first_name AS Manager 
    FROM employees e1
    JOIN employees e2 ON e1.manager_id = e2.employee_id;
    ```

13. **Use common table expressions (CTEs)**
    ```sql
    WITH department_totals AS (
        SELECT department_id, COUNT(*) AS total_employees 
        FROM employees 
        GROUP BY department_id
    )
    SELECT d.department_name, dt.total_employees
    FROM department_totals dt
    JOIN departments d ON dt.department_id = d.department_id;
    ```

14. **Use a CASE statement**
    ```sql
    SELECT first_name, last_name, salary,
           CASE 
               WHEN salary < 50000 THEN 'Low'
               WHEN salary BETWEEN 50000 AND 100000 THEN 'Medium'
               ELSE 'High'
           END AS salary_range
    FROM employees;
    ```

15. **Delete rows from a table**
    ```sql
    DELETE FROM employees WHERE department = 'Sales';
    ```

16. **Update rows in a table**
    ```sql
    UPDATE employees SET salary = salary * 1.10 WHERE department = 'Engineering';
    ```

17. **Insert new rows into a table**
    ```sql
    INSERT INTO employees (first_name, last_name, department, salary) 
    VALUES ('John', 'Doe', 'Marketing', 60000);
    ```

These questions should give you a good range of topics to prepare for an SQL interview. Feel free to practice writing these queries and modifying them to fit different scenarios.
