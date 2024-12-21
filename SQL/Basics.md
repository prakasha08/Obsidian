
### 1. `SELECT`

The `SELECT` statement retrieves specific columns or all columns (`*`) from a table.

**Example:**

```sql
SELECT name, salary FROM employees;
```

Selects only `name` and `salary` columns from the `employees` table.

**Selecting All Columns:**

```sql
SELECT * FROM employees;
```

This returns every column in the `employees` table.

### 2. `FROM`

The `FROM` clause specifies the table(s) where data should come from.

**Example with Multiple Tables (Joining):**

```sql
SELECT employees.name, departments.department_name
FROM employees, departments
WHERE employees.department_id = departments.id;
```

Retrieves names of employees and department names, connecting data across two tables.

### 3. `AS`

`AS` creates an alias (temporary name) for columns or tables, simplifying readability.

**Example of Column Alias:**

```sql
SELECT name AS employee_name, salary AS monthly_salary FROM employees;
```

This renames the `name` column as `employee_name` and `salary` as `monthly_salary` in the results.

**Example of Table Alias:**

```sql
SELECT e.name, d.department_name 
FROM employees AS e, departments AS d 
WHERE e.department_id = d.id;
```

This query uses `e` as an alias for `employees` and `d` for `departments`.

### 4. `DISTINCT`

`DISTINCT` removes duplicate rows in the result set for a specific column or combination of columns.

**Example:**

```sql
SELECT DISTINCT department FROM employees;
```

Returns a unique list of departments without duplicates.

### 5. `AND`

`AND` combines conditions, ensuring all must be true.

**Example:**

```sql
SELECT * FROM employees WHERE age > 30 AND department = 'Sales';
```

Returns employees who are both over 30 and in the Sales department.

### 6. `OR`

`OR` combines conditions where only one must be true.

**Example:**

```sql
SELECT * FROM employees WHERE age < 25 OR department = 'Marketing';
```

Returns employees who are either under 25 or in the Marketing department.

### 7. `NOT`

`NOT` negates a condition, selecting rows where the condition is false.

**Example:**

```sql
SELECT * FROM employees WHERE NOT department = 'HR';
```

Returns employees who are not in the HR department.

### 8. `IN`

`IN` checks if a value matches any value in a list.

**Example:**

```sql
SELECT * FROM employees WHERE department IN ('Sales', 'Marketing', 'IT');
```

Returns employees working in either Sales, Marketing, or IT.

### 9. `BETWEEN`

`BETWEEN` selects values within a specific range, including both endpoints.

**Example:**

```sql
SELECT * FROM employees WHERE salary BETWEEN 3000 AND 6000;
```

Returns employees with salaries between 3000 and 6000.

**Exclusive Range Example:** To exclude endpoints, use greater-than and less-than conditions.

```sql
SELECT * FROM employees WHERE salary > 3000 AND salary < 6000;
```

### 10. `LIKE`

`LIKE` is used for pattern matching. It works with the `%` and `_` wildcards:

- `%` matches any sequence of characters (including none).
- `_` matches exactly one character.

**Examples:**

- Starts with "A": `LIKE 'A%'`
- Ends with "s": `LIKE '%s'`
- Contains "mar": `LIKE '%mar%'`
- Second letter is "e": `LIKE '_e%'`

```sql
SELECT * FROM employees WHERE name LIKE 'A%';
```

Returns employees whose names start with "A."

### 11. `REGEXP` (Regular Expressions)

`REGEXP` allows for more complex pattern matching than `LIKE`.

**Special Characters in REGEXP:**

- `^` – Start of string.
- `$` – End of string.
- `.` – Any single character.
- `*` – Zero or more occurrences of the previous character.
- `+` – One or more occurrences of the previous character.
- `[ ]` – Matches any character within brackets.
- `[a-z]` – Range, matches any lowercase letter.

**Examples:**

- Starts with "A" and ends with "s": `^A.*s$`
- Contains "mar" in the middle: `.*mar.*`
- Name starts with a vowel: `^[AEIOUaeiou]`

```sql
SELECT * FROM employees WHERE name REGEXP '^A.*s$';
```

Returns names starting with "A" and ending with "s."

### 12. `IS NULL`

`IS NULL` checks for `NULL` values in a column.

**Example:**

```sql
SELECT * FROM employees WHERE manager_id IS NULL;
```

Returns employees without a manager (`manager_id` is `NULL`).

### 13. `ORDER BY`

`ORDER BY` sorts results by one or more columns, defaulting to ascending order.

**Example:**

```sql
SELECT * FROM employees ORDER BY age DESC;
```

Sorts employees by age in descending order.

**Multiple Columns:**

```sql
SELECT * FROM employees ORDER BY department ASC, salary DESC;
```

Sorts by department in ascending order, then by salary in descending order.

### 14. `LIMIT`

`LIMIT` restricts the number of rows returned.

**Example:**

```sql
SELECT * FROM employees LIMIT 10;
```

Returns the first 10 rows of the result set.

### 15. `INNER JOIN`

`INNER JOIN` combines rows from two tables based on a common field, returning only matching rows.

**Example:**

```sql
SELECT employees.name, departments.department_name
FROM employees
INNER JOIN departments ON employees.department_id = departments.id;
```

Retrieves employee names with their department names by matching `department_id`.

### 16. `ALIAS`

An alias gives a temporary name to a column or table, simplifying queries.

**Example of Column Alias:**

```sql
SELECT name AS employee_name, salary AS monthly_income FROM employees;
```

**Example of Table Alias:**

```sql
SELECT e.name, d.department_name
FROM employees AS e
INNER JOIN departments AS d ON e.department_id = d.id;
```

Using `e` as an alias for `employees` and `d` for `departments` makes the query shorter and more readable.



### **1. Inner Joins**

An **inner join** retrieves records with matching values in both tables.

#### Example:

```sql
SELECT customers.first_name, orders.order_date
FROM customers
INNER JOIN orders
ON customers.customer_id = orders.customer_id;
```

- Retrieves customers and their order dates.
- Rows without a match in `orders` are excluded.

---

### **2. Joining Across Databases**

You can join tables across different databases by qualifying the database names.

#### Example:

```sql
SELECT db1.customers.first_name, db2.orders.order_date
FROM db1.customers
INNER JOIN db2.orders
ON db1.customers.customer_id = db2.orders.customer_id;
```

- Joins the `customers` table in `db1` with the `orders` table in `db2`.

---

### **3. Self Joins**

A **self-join** joins a table to itself.

#### Example:

```sql
SELECT e1.employee_id, e1.first_name, e2.first_name AS manager_name
FROM employees e1
LEFT JOIN employees e2
ON e1.manager_id = e2.employee_id;
```

- Retrieves employees and their managers.

---

### **4. Joining Multiple Tables**

Joins more than two tables.

#### Example:

```sql
SELECT customers.first_name, orders.order_date, shippers.name AS shipper_name
FROM customers
JOIN orders ON customers.customer_id = orders.customer_id
JOIN shippers ON orders.shipper_id = shippers.shipper_id;
```

- Retrieves customers, their order dates, and the shipper name.

---

### **5. Compound Join Conditions**

Joins tables with multiple conditions.

#### Example:

```sql
SELECT *
FROM employees e
JOIN departments d
ON e.department_id = d.department_id
AND e.hire_date > '2020-01-01';
```

- Joins employees and departments where the department matches and the employee was hired after 2020.

---

### **6. Implicit Join Syntax**

Joins without the `JOIN` keyword (old-style).

#### Example:

```sql
SELECT customers.first_name, orders.order_date
FROM customers, orders
WHERE customers.customer_id = orders.customer_id;
```

- Less readable; not recommended.

---

### **7. Outer Joins**

Includes rows with no match from one or both tables.

#### Example:

**Left Outer Join:**

```sql
SELECT customers.first_name, orders.order_date
FROM customers
LEFT JOIN orders
ON customers.customer_id = orders.customer_id;
```

- Includes all customers, even those without orders.

**Right Outer Join:**

```sql
SELECT orders.order_date, customers.first_name
FROM orders
RIGHT JOIN customers
ON orders.customer_id = customers.customer_id;
```

- Includes all orders, even those without customers.

---

### **8. Outer Join Between Multiple Tables**

Combines multiple outer joins.

#### Example:

```sql
SELECT c.first_name, o.order_date, sh.name AS shipper_name
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id
LEFT JOIN shippers sh ON o.shipper_id = sh.shipper_id;
```

- Includes all customers, their orders (if any), and shipper details.

---

### **9. Self Outer Joins**

Combines self-join with an outer join.

#### Example:

```sql
SELECT e1.first_name, e2.first_name AS manager_name
FROM employees e1
LEFT JOIN employees e2
ON e1.manager_id = e2.employee_id;
```

- Includes all employees, even those without managers.

---

### **10. The USING Clause**

Simplifies join conditions when column names are the same.

#### Example:

```sql
SELECT *
FROM customers
JOIN orders USING (customer_id);
```

- Same as `ON customers.customer_id = orders.customer_id`.

---

### **11. Natural Joins**

Automatically joins tables with matching column names.

#### Example:

```sql
SELECT *
FROM customers
NATURAL JOIN orders;
```

- Joins on columns with the same name.

---

### **12. Cross Joins**

Combines all rows from both tables.

#### Example:

```sql
SELECT *
FROM customers
CROSS JOIN products;
```

- Returns all possible combinations of customers and products.

---

### **13. Unions**

Combines results from multiple `SELECT` queries.

#### Example:

```sql
SELECT first_name FROM customers
UNION
SELECT first_name FROM employees;
```

- Removes duplicates. Use `UNION ALL` to keep duplicates.

---

### **14. Column Attributes**

Defines constraints on columns.

#### Example:

```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    hire_date DATE DEFAULT CURRENT_DATE
);
```

- Adds constraints like `NOT NULL`, `DEFAULT`, `PRIMARY KEY`.

---

### **15. Inserting a Single Row**

Adds one record to a table.

#### Example:

```sql
INSERT INTO customers (first_name, last_name)
VALUES ('John', 'Doe');
```

---

### **16. Inserting Multiple Rows**

Adds several records in one query.

#### Example:

```sql
INSERT INTO customers (first_name, last_name)
VALUES 
('Alice', 'Smith'),
('Bob', 'Brown');
```

---

### **17. Inserting Hierarchical Rows**

Inserts rows with parent-child relationships.

#### Example:

```sql
INSERT INTO departments (department_name)
VALUES ('IT');

INSERT INTO employees (first_name, department_id)
VALUES ('John', LAST_INSERT_ID());
```

---

### **18. Creating a Copy of a Table**

Duplicates a table structure with or without data.

#### Example:

```sql
CREATE TABLE customers_copy AS
SELECT * FROM customers;
```

---

### **19. Updating a Single Row**

Modifies one record.

#### Example:

```sql
UPDATE customers
SET first_name = 'Alice'
WHERE customer_id = 1;
```

---

### **20. Updating Multiple Rows**

Updates multiple records.

#### Example:

```sql
UPDATE employees
SET salary = salary * 1.1
WHERE department_id = 2;
```

---

### **21. Using Subqueries in Updates**

Uses a query to compute updated values.

#### Example:

```sql
UPDATE employees
SET salary = salary + (SELECT AVG(salary) FROM employees)
WHERE department_id = 1;
```

---

### **22. Deleting Rows**

Removes records.

#### Example:

```sql
DELETE FROM customers
WHERE last_name = 'Doe';
```

---

### **23. Restoring Course Database**

Recreates a database from a backup.

#### Example:

```sql
SOURCE /path/to/backup.sql;
```

---

Let me know if you want deeper explanations or further examples for any specific topic!