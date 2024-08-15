# Questions

## Triggers and views

A trigger is a special type of stored procedure that automatically executes when certain events occur in the database. These events could be INSERT, UPDATE, or DELETE operations on a table

```sql
CREATE TRIGGER SalaryCap
BEFORE INSERT OR UPDATE ON Employees
FOR EACH ROW
BEGIN
    IF NEW.Salary > 100000 THEN
        SET NEW.Salary = 100000;
    END IF;
END;
```

### Views

A view is a virtual table in SQL that is based on the result set of a SELECT query. Views do not store data physically but display data stored in one or more underlying tables

```sql
CREATE VIEW ActiveCustomers AS
SELECT CustomerID, CustomerName, Status
FROM Customers
WHERE Status = 'Active';

SELECT * FROM ActiveCustomers;

UPDATE ActiveCustomers
SET Status = 'Inactive'
WHERE CustomerID = 101;
```

## SQL Diff Queries

```sql
SELECT book.title, author.name
FROM book
JOIN author ON book.author_id = author.author_id;

SELECT author.name, book.title 
FROM book 
JOIN author ON book.author_id = author.author_id 
WHERE book.publish_year > 2005;
```

## Aggregate Functions

```sql
-- COUNT
SELECT COUNT(*) AS total_books
FROM book;

-- SUM
SELECT SUM(price) AS total_revenue
FROM sales;

-- AVG
SELECT AVG(salary) AS average_salary
FROM employees;

-- MIN
SELECT MIN(salary) AS lowest_salary
FROM employees;

-- MAX
SELECT MAX(salary) AS highest_salary
FROM employees;

-- Group By
SELECT product_id, SUM(amount) AS total_revenue
FROM sales
GROUP BY product_id;
```

## Assertions

```sql
-- Assertions
CREATE ASSERTION TotalSalaryConstraint
CHECK (
    NOT EXISTS (
        SELECT department_id
        FROM Employees
        GROUP BY department_id
        HAVING SUM(salary) > 1000000
    )
);
```

## Alter Table

```sql
-- 1. Add a new column 'date_of_birth' of type DATE to the 'Employees' table
ALTER TABLE Employees 
ADD date_of_birth DATE;

-- 2. Drop the existing column 'middle_name' from the 'Employees' table
ALTER TABLE Employees 
DROP COLUMN middle_name;

-- 3. Modify the data type of the 'salary' column to DECIMAL(10, 2)
ALTER TABLE Employees 
MODIFY salary DECIMAL(10, 2);

-- 4. Rename the column 'emp_id' to 'employee_id' in the 'Employees' table
ALTER TABLE Employees 
RENAME COLUMN emp_id TO employee_id;

-- 5. Add a UNIQUE constraint to the 'email' column in the 'Employees' table
ALTER TABLE Employees 
ADD CONSTRAINT emp_unique UNIQUE (email);

-- 6. Drop the UNIQUE constraint named 'emp_unique' from the 'Employees' table
ALTER TABLE Employees 
DROP CONSTRAINT emp_unique;

-- 7. Rename the 'Employees' table to 'Staff'
ALTER TABLE Employees 
RENAME TO Staff;

-- 8. Modify the 'phone_number' column to be NOT NULL in the 'Employees' table
ALTER TABLE Employees 
MODIFY phone_number VARCHAR(15) NOT NULL;

-- 9. Add a default value 'Active' for the 'status' column in the 'Employees' table
ALTER TABLE Employees 
ALTER COLUMN status SET DEFAULT 'Active';

-- 10. Remove the default value from the 'status' column in the 'Employees' table
ALTER TABLE Employees 
ALTER COLUMN status DROP DEFAULT;
```
