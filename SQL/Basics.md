
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