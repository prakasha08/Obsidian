
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


### **CASE Statement in SQL**

The `CASE` statement in SQL is used for conditional logic within SQL queries. It works like an `IF-ELSE` statement in programming languages. You can use it to return different values based on conditions.

---

#### **Syntax of CASE**

There are two main types of `CASE` expressions in SQL:

#### **1. Simple CASE Expression**

This compares a column or expression against multiple values and returns a result.

```sql
CASE column_name
    WHEN value1 THEN result1
    WHEN value2 THEN result2
    ELSE default_result
END
```

#### **2. Searched CASE Expression**

This evaluates multiple conditions and returns a result based on the first `TRUE` condition.

```sql
CASE 
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    ELSE default_result
END
```

---

#### **Examples**

#### **Example 1: Using Simple CASE**

Let's say we have a `students` table:

|student_id|name|grade|
|---|---|---|
|1|Alex|A|
|2|Bob|B|
|3|Chris|C|
|4|David|A|

We want to classify students based on their grades:

```sql
SELECT name, grade,
    CASE grade
        WHEN 'A' THEN 'Excellent'
        WHEN 'B' THEN 'Good'
        WHEN 'C' THEN 'Average'
        ELSE 'Needs Improvement'
    END AS performance
FROM students;
```

**Output:**

|name|grade|performance|
|---|---|---|
|Alex|A|Excellent|
|Bob|B|Good|
|Chris|C|Average|
|David|A|Excellent|

---

#### **Example 2: Using Searched CASE**

Suppose we have an `employees` table:

|emp_id|name|salary|
|---|---|---|
|1|Alice|90000|
|2|Bob|75000|
|3|Charlie|50000|
|4|David|30000|

We want to categorize employees based on their salary:

```sql
SELECT name, salary,
    CASE 
        WHEN salary >= 80000 THEN 'High Salary'
        WHEN salary >= 50000 THEN 'Medium Salary'
        ELSE 'Low Salary'
    END AS salary_category
FROM employees;
```

**Output:**

|name|salary|salary_category|
|---|---|---|
|Alice|90000|High Salary|
|Bob|75000|Medium Salary|
|Charlie|50000|Medium Salary|
|David|30000|Low Salary|

---

#### **Using CASE in ORDER BY**

You can also use `CASE` in `ORDER BY` to define custom sorting:

```sql
SELECT name, grade
FROM students
ORDER BY 
    CASE grade 
        WHEN 'A' THEN 1
        WHEN 'B' THEN 2
        WHEN 'C' THEN 3
        ELSE 4
    END;
```

This sorts `A` grades first, then `B`, then `C`.

---

#### **Using CASE in UPDATE**

You can use `CASE` in an `UPDATE` statement:

```sql
UPDATE employees
SET salary = 
    CASE 
        WHEN salary < 40000 THEN salary + 5000
        WHEN salary BETWEEN 40000 AND 70000 THEN salary + 3000
        ELSE salary + 2000
    END;
```

This increases salary based on different conditions.

---

#### **Conclusion**

- `CASE` helps in conditional logic inside SQL queries.
- It works in `SELECT`, `ORDER BY`, `UPDATE`, and `WHERE` clauses.
- It is similar to `IF-ELSE` statements in programming.

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

### **🔹 LEFT JOIN in SQL (with a Clear Example)**

A **LEFT JOIN** in SQL returns **all rows from the left table** and **matching rows from the right table**. If there is **no match in the right table, NULL values** are returned for columns from the right table.

---

### **📌 Example Scenario**

We have two tables:  
1️⃣ `students` → Contains student details  
2️⃣ `courses` → Contains course details

#### **🔹 students Table**

|student_id|name|age|
|---|---|---|
|1|Alice|22|
|2|Bob|23|
|3|John|24|
|4|Emma|21|

#### **🔹 courses Table**

|course_id|student_id|course_name|
|---|---|---|
|101|1|Math|
|102|2|Science|
|103|4|History|

---

### **🔹 LEFT JOIN Query**

```sql
SELECT students.student_id, students.name, courses.course_name
FROM students
LEFT JOIN courses ON students.student_id = courses.student_id;
```

---

### **🔹 Output of the Query**

|student_id|name|course_name|
|---|---|---|
|1|Alice|Math|
|2|Bob|Science|
|3|John|NULL|
|4|Emma|History|

---

### **🔹 Explanation**

- **Alice (ID=1)** → Has a course ("Math") ✅
- **Bob (ID=2)** → Has a course ("Science") ✅
- **Emma (ID=4)** → Has a course ("History") ✅
- **John (ID=3)** → Has **no matching course** in the `courses` table, so `NULL` appears in the `course_name` column ❌

---

### **🔹 Key Points**

✅ **Returns all records from the left table (`students`)**  
✅ **Matches records from the right table (`courses`)**  
✅ **If there is no match, NULL is returned for the right table columns**

Would you like an example with real SQL execution? 🚀

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

### **🔹 SELF JOIN in SQL (with Clear Explanation & Example)**

A **SELF JOIN** is when a table joins with **itself**. This is useful for hierarchical relationships like **employees & managers**, **students & mentors**, or **parent-child relationships**.

---

### **📌 Example Scenario: Employee-Manager Relationship**

We have a **single table `employees`** where each employee has a **manager_id** (which refers to another employee in the same table).

#### **🔹 employees Table**

|employee_id|name|manager_id|
|---|---|---|
|1|Alice|NULL|
|2|Bob|1|
|3|John|1|
|4|Emma|2|
|5|Chris|2|

### **🔹 SELF JOIN Query**

```sql
SELECT e1.employee_id AS EmployeeID, e1.name AS Employee, 
       e2.employee_id AS ManagerID, e2.name AS Manager
FROM employees e1
LEFT JOIN employees e2 
ON e1.manager_id = e2.employee_id;
```

---

### **🔹 Output of the Query**

|EmployeeID|Employee|ManagerID|Manager|
|---|---|---|---|
|1|Alice|NULL|NULL|
|2|Bob|1|Alice|
|3|John|1|Alice|
|4|Emma|2|Bob|
|5|Chris|2|Bob|

---

### **🔹 Explanation**

1️⃣ **Alice (ID=1)** has no manager (`NULL`).  
2️⃣ **Bob (ID=2) & John (ID=3)** report to **Alice (ID=1)**.  
3️⃣ **Emma (ID=4) & Chris (ID=5)** report to **Bob (ID=2)**.

---

### **🔹 Key Points**

✅ **SELF JOIN treats a table like two different tables** using aliases (`e1` & `e2`).  
✅ Used for **hierarchical data** like employees-managers, students-mentors, etc.  
✅ Can be `INNER JOIN` (only matched results) or `LEFT JOIN` (keep all employees, even without a manager).

Would you like an example with another dataset? 🚀

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

### **What is a CROSS JOIN?**

A **CROSS JOIN** produces a **Cartesian Product** of two tables, meaning **each row from the first table is combined with every row from the second table**.

🔹 **Key Points:**

- **No ON condition is used** (unlike INNER/LEFT/RIGHT JOIN).
- If **Table A has `m` rows** and **Table B has `n` rows**, the result will have **`m × n` rows**.
- It is useful for **generating combinations of values**.

---

## **🔹 Example Scenario: University Database**

Consider two tables:

### **🔹 students Table**

|student_id|name|
|---|---|
|1|Alice|
|2|Bob|
|3|John|

### **🔹 courses Table**

|course_id|course_name|
|---|---|
|101|Math|
|102|Physics|

---

## **🔹 CROSS JOIN Example**

**Goal:** Get **all possible combinations** of students and courses.

sql

CopyEdit

`SELECT students.name, courses.course_name FROM students CROSS JOIN courses;`

### **🔹 Output**

|name|course_name|
|---|---|
|Alice|Math|
|Alice|Physics|
|Bob|Math|
|Bob|Physics|
|John|Math|
|John|Physics|

#### **🔹 Explanation**

- **Every student is paired with every course.**
- **3 students × 2 courses = 6 rows in output.**

---

## **🔹 When to Use CROSS JOIN?**

✅ **Generating all possible combinations** (e.g., students & courses, products & discounts, etc.).  
✅ **Simulating permutations** where each item in one table must be paired with all items in another.  
✅ **Filling missing data by creating all possible pairs before filtering out unwanted ones.**

---
### **🔹 RIGHT JOIN and FULL JOIN (With Clear Examples)**

#### **📌 What are RIGHT JOIN & FULL JOIN?**

- **RIGHT JOIN** → Returns **all records from the right table** and **only matching records from the left table**. If there is no match, it fills `NULL` for the left table's columns.
- **FULL JOIN** (or **FULL OUTER JOIN**) → Returns **all records from both tables**, filling `NULL` where there is no match.

---

### **🔹 Example Scenario: University Database**

We use the same **`students`** and **`courses`** tables from earlier but focus only on these:

#### **🔹 students Table**

|student_id|name|
|---|---|
|1|Alice|
|2|Bob|
|3|John|

#### **🔹 enrollments Table**

|student_id|course_id|
|---|---|
|1|101|
|1|102|
|3|101|
|4|103|

🔹 **Notice:**

- **Student 2 (Bob)** is **not enrolled** in any course.
- **Student 4 (not in `students` table)** appears in `enrollments`.

---

## **🔹 RIGHT JOIN Example**

**Goal:** Get all enrollments and include student details if available.

```sql
SELECT students.student_id, students.name, enrollments.course_id
FROM students
RIGHT JOIN enrollments ON students.student_id = enrollments.student_id;
```

### **🔹 Output**

|student_id|name|course_id|
|---|---|---|
|1|Alice|101|
|1|Alice|102|
|3|John|101|
|NULL|NULL|103|

#### **🔹 Explanation**

- Students **1 (Alice) & 3 (John)** match and are displayed with their courses. ✅
- **Course 103 has a student (ID=4) not in `students`, so NULL appears for `student_id` & `name`**. ❌

---

## **🔹 FULL JOIN (FULL OUTER JOIN) Example**

**Goal:** Get **all students and all enrollments**, even if there is **no match**.

```sql
SELECT students.student_id, students.name, enrollments.course_id
FROM students
FULL JOIN enrollments ON students.student_id = enrollments.student_id;
```

### **🔹 Output**

|student_id|name|course_id|
|---|---|---|
|1|Alice|101|
|1|Alice|102|
|2|Bob|NULL|
|3|John|101|
|NULL|NULL|103|

#### **🔹 Explanation**

- **Students Alice & John** match their enrollments. ✅
- **Bob (ID=2) has no enrollments, so `NULL` appears in `course_id`**. ❌
- **Course 103 (student ID=4) has no matching student, so `NULL` appears for `student_id` & `name`**. ❌

---

## **🔹 When to Use?**

✅ **RIGHT JOIN** → When you need **all records from the right table** and matching records from the left.  
✅ **FULL JOIN** → When you need **all data from both tables, even if there is no match**.

Would you like an example with more complex conditions? 🚀
## **🔹 Difference from Other Joins**

| Join Type      | Behavior                                                                    |
| -------------- | --------------------------------------------------------------------------- |
| **INNER JOIN** | Returns only matching records.                                              |
| **LEFT JOIN**  | Returns all left table records + matching right table records.              |
| **RIGHT JOIN** | Returns all right table records + matching left table records.              |
| **FULL JOIN**  | Returns all records from both tables (fills NULLs for no matches).          |
| **CROSS JOIN** | Returns **every combination** of rows from both tables (Cartesian Product). |

### **📌 What is UNION?**

The **`UNION`** operator is used to **combine the results of two or more `SELECT` queries** into a single result set.

🔹 **Key Rules of `UNION`:**

1. **Both `SELECT` queries must have the same number of columns**.
2. **The columns must have compatible data types**.
3. **By default, `UNION` removes duplicate rows**.
4. Use **`UNION ALL`** to include duplicates.

---

## **🔹 Example Scenario: University Database**

We have two tables:

### **🔹 students_2023 Table**

|student_id|name|
|---|---|
|1|Alice|
|2|Bob|
|3|John|

### **🔹 students_2024 Table**

|student_id|name|
|---|---|
|3|John|
|4|Emma|
|5|David|

---

## **🔹 Example 1: Using `UNION` (Removes Duplicates)**

We want a **list of all unique students** from both tables.

```sql
SELECT student_id, name FROM students_2023
UNION
SELECT student_id, name FROM students_2024;
```

### **🔹 Output**

|student_id|name|
|---|---|
|1|Alice|
|2|Bob|
|3|John|
|4|Emma|
|5|David|

#### **🔹 Explanation**

- **John (student_id=3) appeared in both tables, but UNION removes duplicates.**
- The result contains **only unique records**.

---

## **🔹 Example 2: Using `UNION ALL` (Includes Duplicates)**

If we **want to keep duplicates**, use `UNION ALL`:

```sql
SELECT student_id, name FROM students_2023
UNION ALL
SELECT student_id, name FROM students_2024;
```

### **🔹 Output**

|student_id|name|
|---|---|
|1|Alice|
|2|Bob|
|3|John|
|3|John|
|4|Emma|
|5|David|

#### **🔹 Explanation**

- **John appears twice** because we used `UNION ALL`.
- `UNION ALL` **does not remove duplicates**.

---

## **🔹 When to Use?**

✅ **`UNION`** → When you **want only unique results** (removes duplicates).  
✅ **`UNION ALL`** → When you **want all results, including duplicates**.

Would you like an example where `UNION` is used with additional filtering? 🚀

---

## ** GROUP BY – What is it?**

**`GROUP BY`** is used to **group rows** that have the same values in a specified column. After grouping, we can use **aggregate functions** like `COUNT()`, `SUM()`, `AVG()`, `MAX()`, `MIN()`, etc., to perform calculations on each group.

### **🔹 Syntax**

```sql
SELECT column_name, AGGREGATE_FUNCTION(column_name)
FROM table_name
GROUP BY column_name;
```

- `column_name`: The column on which we are grouping.
- `AGGREGATE_FUNCTION()`: A function like `SUM()`, `AVG()`, `COUNT()`, etc.
- `GROUP BY column_name`: Groups the rows based on that column.

---

### **📌 Example 1: Counting Employees in Each Department**

#### **👨‍💻 Sample `employees` Table**

|employee_id|name|department|salary|
|---|---|---|---|
|1|Alice|IT|50,000|
|2|Bob|HR|60,000|
|3|John|IT|55,000|
|4|Emma|HR|70,000|
|5|Max|IT|65,000|

#### **✅ Query: Count the number of employees in each department**

```sql
SELECT department, COUNT(*) AS num_employees
FROM employees
GROUP BY department;
```

#### **🔹 Output**

|department|num_employees|
|---|---|
|IT|3|
|HR|2|

✅ **Explanation**:

- It **groups** all employees by `department`.
- Then, it **counts** the number of employees in each group.

---

### **📌 Example 2: Find the Average Salary for Each Department**

```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department;
```

#### **🔹 Output**

|department|avg_salary|
|---|---|
|IT|56,666.67|
|HR|65,000|

✅ **Explanation**:

- The salaries for **IT**: (50,000 + 55,000 + 65,000) / 3 = **56,666.67**
- The salaries for **HR**: (60,000 + 70,000) / 2 = **65,000**

---

## **2️⃣ HAVING – What is it?**

The **HAVING** clause is used to **filter grouped results** after applying `GROUP BY`.

- It is **similar to `WHERE`**, but **WHERE works on individual rows**, whereas **HAVING works on groups**.

### **🔹 Syntax**

```sql
SELECT column_name, AGGREGATE_FUNCTION(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

- `HAVING condition`: Specifies the condition for filtering the grouped results.

---

### **📌 Example 3: Show Only Departments Where More Than 2 Employees Work**

```sql
SELECT department, COUNT(*) AS num_employees
FROM employees
GROUP BY department
HAVING COUNT(*) > 2;
```

#### **🔹 Output**

|department|num_employees|
|---|---|
|IT|3|

✅ **Explanation**:

- It first groups the data by `department`.
- Then, it **counts employees** in each department.
- The `HAVING COUNT(*) > 2` **filters out** departments where employees are 2 or fewer.

---

### **📌 Example 4: Show Only Departments Where the Average Salary is Above 60,000**

```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 60000;
```

#### **🔹 Output**

|department|avg_salary|
|---|---|
|HR|65,000|

✅ **Explanation**:

- It calculates **average salary** for each department.
- It filters out departments where `AVG(salary) > 60000`.

---

## **3️⃣ Difference Between WHERE and HAVING**

|Feature|WHERE|HAVING|
|---|---|---|
|Used for|Filtering individual rows|Filtering groups (after `GROUP BY`)|
|Works on|Single row at a time|Aggregated results|
|Aggregate functions allowed?|❌ No|✅ Yes|

---

## **4️⃣ WHEN TO USE GROUP BY AND HAVING?**

- Use **`GROUP BY`** when you need to **summarize data**.
- Use **`HAVING`** when you need to **filter grouped data**.

---

## **5️⃣ Real-Life Example**

### **📌 Example 5: Finding High-Revenue Customers**

#### **👨‍💻 Sample `orders` Table**

|order_id|customer_name|total_amount|
|---|---|---|
|1|Alice|200|
|2|Bob|450|
|3|Alice|300|
|4|Bob|500|
|5|John|150|

#### **✅ Query: Find customers whose total spending is more than $500**

```sql
SELECT customer_name, SUM(total_amount) AS total_spent
FROM orders
GROUP BY customer_name
HAVING SUM(total_amount) > 500;
```

#### **🔹 Output**

|customer_name|total_spent|
|---|---|
|Bob|950|

✅ **Explanation**:

- It **groups orders by `customer_name`**.
- It **calculates total spending** for each customer.
- It **filters out customers who spent less than 500**.

---

## **6️⃣ Final Summary**

|Clause|Purpose|
|---|---|
|**GROUP BY**|Groups data based on one or more columns|
|**HAVING**|Filters grouped data (works **after** GROUP BY)|
|**WHERE**|Filters individual rows (works **before** GROUP BY)|

---

## **🎯 Quick Practice Questions**

Try these queries to test your understanding:

1. **Find the total salary paid to each department** in the `employees` table.
2. **Find departments where the number of employees is greater than 3**.
3. **Find customers who have placed more than 2 orders**.

Would you like me to explain any part again? 🚀
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

## **🔹 SQL Subqueries (With Clear Examples)**

A **subquery** is a SQL query **inside another query**. It can be used in **`SELECT`**, **`FROM`**, **`WHERE`**, or **`HAVING`** clauses.

---

## **🔹 Types of Subqueries**

### 1️⃣ **Subquery in `SELECT` (Scalar Subquery)**

- Used to **fetch a single value** and use it in the main query.

### 2️⃣ **Subquery in `WHERE` (Filtering Condition)**

- Used to **filter results based on another query**.

### 3️⃣ **Subquery in `FROM` (Derived Table)**

- Used to **treat a subquery result as a table**.

### 4️⃣ **Subquery in `HAVING` (Filtering Groups)**

- Used to **filter grouped data**.

---

## **🔹 1️⃣ Subquery in `SELECT` Clause**

**Goal:** Find employee salaries and how they compare to the **average salary**.

```sql
SELECT name, salary, 
       (SELECT AVG(salary) FROM employees) AS avg_salary
FROM employees;
```

### **🔹 Output**

|name|salary|avg_salary|
|---|---|---|
|Alice|50,000|58,750|
|Bob|60,000|58,750|
|John|55,000|58,750|
|Emma|70,000|58,750|

✅ **The subquery calculates the average salary** and displays it in each row.

---

## **🔹 2️⃣ Subquery in `WHERE` Clause**

**Goal:** Get employees earning **above the average salary**.

```sql
SELECT name, salary 
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

### **🔹 Output**

|name|salary|
|---|---|
|Bob|60,000|
|Emma|70,000|

✅ **The subquery calculates the average salary**, and the main query filters employees with higher salaries.

---

## **1️⃣ Subquery in `FROM` Clause (Derived Table)**

### **🔹 Query Breakdown**

```sql
SELECT department_id, avg_salary 
FROM (
    SELECT department_id, AVG(salary) AS avg_salary
    FROM employees 
    GROUP BY department_id
) AS dept_avg;
```

### **🔹 What This Query Does**

1. **Inner Query (Subquery)**
    
    ```sql
    SELECT department_id, AVG(salary) AS avg_salary
    FROM employees 
    GROUP BY department_id;
    ```
    
    - This **groups** employees by `department_id`.
    - It calculates the **average salary** for each department.
2. **Outer Query**
    
    ```sql
    SELECT department_id, avg_salary 
    FROM (...) AS dept_avg;
    ```
    
    - The **outer query** selects the `department_id` and `avg_salary` from the **subquery result**.

---

### **🔹 Example with Data**

#### **👨‍💻 Sample `employees` Table**

|employee_id|name|salary|department_id|
|---|---|---|---|
|1|Alice|50,000|1|
|2|Bob|60,000|2|
|3|John|55,000|1|
|4|Emma|70,000|3|

#### **🔹 Step 1: Subquery Result (Average Salary per Department)**

|department_id|avg_salary|
|---|---|
|1|52,500|
|2|60,000|
|3|70,000|

#### **🔹 Step 2: Outer Query Reads the Table**

- The main query **fetches results from this derived table** and displays them.

### **🔹 Final Output**

|department_id|avg_salary|
|---|---|
|1|52,500|
|2|60,000|
|3|70,000|

✅ **This method is useful when you need to compute something first and then filter or process it further.**

---

## **2️⃣ Subquery in `HAVING` Clause**

### **🔹 Query Breakdown**

```sql
SELECT department_id, AVG(salary) AS avg_salary
FROM employees
GROUP BY department_id
HAVING AVG(salary) > (SELECT AVG(salary) FROM employees);
```

### **🔹 Understanding `HAVING`**

- The `HAVING` clause is **like `WHERE` but for grouped data**.
- `WHERE` filters **individual rows**, while `HAVING` filters **grouped results**.

---

### **🔹 Step-by-Step Execution**

#### **Step 1: Find Overall Average Salary**

```sql
SELECT AVG(salary) FROM employees;
```

- Total salaries: **50,000 + 60,000 + 55,000 + 70,000 = 235,000**
- Employee count: **4**
- **Global average salary:** 235,000÷4=58,750235,000 \div 4 = 58,750

#### **Step 2: Compute Department-Wise Average**

```sql
SELECT department_id, AVG(salary) AS avg_salary
FROM employees
GROUP BY department_id;
```

|department_id|avg_salary|
|---|---|
|1|52,500|
|2|60,000|
|3|70,000|

#### **Step 3: Apply `HAVING` Clause**

```sql
HAVING AVG(salary) > 58,750;
```

- Only **departments with an average salary greater than 58,750** are kept.
- Department **1 is removed** because 52,500 < 58,750.

---

### **🔹 Final Output**

|department_id|avg_salary|
|---|---|
|3|70,000|

✅ **Only department 3 remains because its average salary (70,000) is greater than the global average salary (58,750).**

---

## **🔹 Key Takeaways**

### **📌 Subquery in `FROM` (Derived Table)**

✔ The **subquery acts as a temporary table**.  
✔ Useful when you need to **precompute** something and use it in the main query.

### **📌 Subquery in `HAVING` (Filtering Groups)**

✔ `HAVING` is used **after `GROUP BY`** to filter grouped results.  
✔ `HAVING AVG(salary) > (SELECT AVG(salary))` **compares each department’s average salary to the overall average**.

---

## **🔹 Summary Table**

|**Type**|**When to Use?**|**Example Use Case**|
|---|---|---|
|**Subquery in `FROM`**|When you need to **create a temporary table** for further filtering|Find **average salary per department**|
|**Subquery in `HAVING`**|When you need to **filter groups** based on a condition|Find **departments where the avg salary is above the global avg**|

Would you like more examples or clarification on any part? 🚀
## **🔹 Key Takeaways**

✔ **Subqueries help perform nested calculations**.  
✔ Can be used in **`SELECT`**, **`WHERE`**, **`FROM`**, and **`HAVING`**.  
✔ Can return **single values (scalar subqueries)** or **multiple values (table subqueries)**.



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