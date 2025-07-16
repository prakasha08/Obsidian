
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

### 🔹 `ANY` Operator

The `ANY` keyword compares a value to **any value in a list or subquery** — meaning **"at least one"** must match the condition.

### ✅ Syntax:

sql

CopyEdit

`<value> <operator> ANY (<subquery>)`

### ✅ Meaning:

It returns `TRUE` if the comparison is `TRUE` **for at least one** value in the subquery.

### 📌 Example 1: Using `ANY` with `>`

**Question**: Find employees who earn **more than at least one** employee in department 30.

sql

CopyEdit

`SELECT name FROM employees WHERE salary > ANY (     SELECT salary     FROM employees     WHERE department_id = 30 );`

🔍 **What happens**:

- The subquery fetches all salaries in department 30.
    
- The outer query finds employees whose salary is **greater than at least one** of those salaries.
    

---

### 🔹 `ALL` Operator

The `ALL` keyword compares a value to **every value** in a list or subquery — meaning **"must satisfy the condition for all values"**.

#### ✅ Syntax:

sql

CopyEdit

`<value> <operator> ALL (<subquery>)`

#### ✅ Meaning:

It returns `TRUE` if the comparison is `TRUE` **for every** value in the subquery.

#### 📌 Example 2: Using `ALL` with `>`

**Question**: Find employees who earn **more than every** employee in department 30.

sql

CopyEdit

`SELECT name FROM employees WHERE salary > ALL (     SELECT salary     FROM employees     WHERE department_id = 30 );`

🔍 **What happens**:

- The subquery fetches all salaries in department 30.
    
- The outer query finds employees whose salary is **greater than the highest** salary from that list.
    

---

### 🔁 Comparison: `ANY` vs `ALL`

| Operator | Means…               | Returns TRUE if…                                     |
| -------- | -------------------- | ---------------------------------------------------- |
| `ANY`    | At least one matches | **One or more** values in subquery satisfy condition |
| `ALL`    | All must match       | **Every** value in subquery satisfies condition      |

---

#### 📌 More Examples

#### Using `= ANY` (same as `IN`)

sql

CopyEdit

`SELECT name FROM employees WHERE department_id = ANY (10, 20, 30);`

🔸 This works like:

sql

CopyEdit

`WHERE department_id IN (10, 20, 30);`

---

#### Using `!= ALL` (not equal to all → i.e., different from every value)

sql

CopyEdit

`SELECT name FROM employees WHERE department_id != ALL (10, 20, 30);`

🔸 This means: department_id is **not equal to 10, 20, or 30** — different from **every** listed value.

---

#### ⚠️ Things to Note

- If the subquery returns **no rows**, then:
    
    - `x > ANY (empty)` → `FALSE`
        
    - `x > ALL (empty)` → `TRUE` (vacuously true)
        
- Use `ALL` carefully — it’s **stricter** than `ANY`.
    

---

#### 💡 Tip

| Use `ANY` when:                                                          | Use `ALL` when:                                     |
| ------------------------------------------------------------------------ | --------------------------------------------------- |
| You want to check if a value is greater/less than **any** value in a set | You want to check if it’s greater/less than **all** |
| You're okay if **one** match works                                       | You need it to satisfy **all**                      |
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

| LIKE Operator                | Description                                                                  |
| ---------------------------- | ---------------------------------------------------------------------------- |
| WHERE first_name LIKE 'a%'   | Finds any values that start with "a"                                         |
| WHERE first_name LIKE '%a'   | Finds any values that end with "a"                                           |
| WHERE first_name LIKE '%or%' | Finds any values that have "or" in any position                              |
| WHERE first_name LIKE '_r%'  | Finds any values that have "r" in the second position                        |
| WHERE first_name LIKE 'a_%'  | Finds any values that start with "a" and are at least 2 characters in length |
| WHERE first_name LIKE 'a__%' | Finds any values that start with "a" and are at least 3 characters in length |
| WHERE first_name LIKE 'a%o'  | Finds any values that start with "a" and ends with "o"                       |
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
#### ✅ 1. `^` – Start of String

#### 📘 Meaning:

Matches only if the **pattern begins** at the **start** of the string.

##### ✅ Example:

`SELECT 'apple' REGEXP '^a';  -- ✅ 1 (matches) SELECT 'banana' REGEXP '^a'; -- ❌ 0 (does not start with 'a')`

---

#### ✅ 2. `$` – End of String

#### 📘 Meaning:

Matches only if the **pattern ends** at the **end** of the string.

##### ✅ Example:

sql

CopyEdit

`SELECT 'banana' REGEXP 'a$';   -- ✅ 1 (ends with 'a') SELECT 'grape' REGEXP 'a$';    -- ❌ 0`

---

#### ✅ 3. `.` – Any Single Character

#### 📘 Meaning:

Matches **exactly one character** of any kind (except line breaks).

##### ✅ Example:

`SELECT 'cat' REGEXP 'c.t';     -- ✅ 1 (matches 'c' + any char + 't') SELECT 'cut' REGEXP 'c.t';     -- ✅ 1 SELECT 'ct'  REGEXP 'c.t';     -- ❌ 0 (missing middle character)`

---

#### ✅ 4. `*` – Zero or More Occurrences of Previous Character

#### 📘 Meaning:

Matches **zero or more times** of the character **just before the `*`**.

##### ✅ Example:

sql

CopyEdit

`SELECT 'baaaa' REGEXP 'ba*';   -- ✅ 1 (matches 'b' + any number of 'a') SELECT 'b'     REGEXP 'ba*';   -- ✅ 1 (zero 'a') SELECT 'bc'    REGEXP 'ba*';   -- ✅ 1 (zero 'a') SELECT 'bac'   REGEXP 'ba*';   -- ✅ 1 SELECT 'bccc'  REGEXP 'ba*';   -- ❌ 0 ('a' missing)`

---

#### 5. `+` – One or More Occurrences of Previous Character

#### 📘 Meaning:

Matches **at least one** of the previous character.

##### ✅ Example:

`SELECT 'baaaa' REGEXP 'ba+';   -- ✅ 1 (at least one 'a') SELECT 'ba'    REGEXP 'ba+';   -- ✅ 1 SELECT 'b'     REGEXP 'ba+';   -- ❌ 0 ('a' is required at least once)`

---

#### ✅ 6. `[ ]` – Character Class

##### 📘 Meaning:

Matches **any one character** inside the brackets.

##### ✅ Example:

sql

CopyEdit

`SELECT 'cat' REGEXP 'c[aeiou]t'; -- ✅ 1 ('a' is in the set) SELECT 'cot' REGEXP 'c[aeiou]t'; -- ✅ 1 ('o' is in the set) SELECT 'cpt' REGEXP 'c[aeiou]t'; -- ❌ 0 ('p' is not in the set)`

---

#### ✅ 7. `[a-z]` – Character Range

##### 📘 Meaning:

Matches **any one character** from the given range (`a` to `z` lowercase).

##### ✅ Example:

sql

CopyEdit

`SELECT 'hello' REGEXP '[a-z]';   -- ✅ 1 (has lowercase letters) SELECT '1234'  REGEXP '[a-z]';   -- ❌ 0 (no letters) SELECT 'H'     REGEXP '[a-z]';   -- ❌ 0 (uppercase is not matched)`

---

#### ✅ Extra: Combine Them Together

##### Example 1:

sql

CopyEdit

`SELECT 'abc123' REGEXP '^[a-z]+[0-9]+$'; -- ✅ Starts with letters, ends with numbers -- ✅ Output: 1`

##### ✅ Example 2:

sql

CopyEdit

`SELECT 'a.b-c@leetcode.com' REGEXP '^[a-zA-Z][a-zA-Z0-9_.-]*@leetcode\\.com$'; -- ✅ Full email pattern with rules -- ✅ Output: 1`

---

#### 🧠 Summary Table

| Symbol  | Meaning                                | Example Pattern | Matches Example     |
| ------- | -------------------------------------- | --------------- | ------------------- |
| `^`     | Start of string                        | `^a`            | `'apple'`           |
| `$`     | End of string                          | `a$`            | `'banana'`          |
| `.`     | Any one character                      | `c.t`           | `'cat', 'cut'`      |
| `*`     | Zero or more of the previous character | `ba*`           | `'b', 'ba', 'baaa'` |
| `+`     | One or more of the previous character  | `ba+`           | `'ba', 'baaa'`      |
| `[abc]` | One of a set of characters             | `c[aeiou]t`     | `'cat', 'cot'`      |
| `[a-z]` | Range of characters                    | `[a-z]`         | `'hello'`           |
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


### `OFFSET` in SQL – Skip Rows in Result Set

#### 🔹 **Purpose**:

`OFFSET` is used to **skip a specific number of rows** before starting to return results from a query.

---

#### ✅ Syntax:

```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column_name
LIMIT n OFFSET m;
```

- `LIMIT n` → Returns **n** rows
    
- `OFFSET m` → **Skips m** rows before returning data
    

> 🧠 Think of `OFFSET m` as telling SQL:  
> “**Ignore the first `m` rows**, then give me the next `n` rows.”

---

#### 📘 Example Table: `Employees`

|id|name|salary|
|---|---|---|
|1|Alice|5000|
|2|Bob|7000|
|3|Carol|6000|
|4|David|8000|
|5|Emma|9000|

---

##### ✅ Example 1: Skip the first row

```sql
SELECT name, salary
FROM Employees
ORDER BY salary DESC
LIMIT 1 OFFSET 1;
```

##### 🔍 Explanation:

1. `ORDER BY salary DESC`: Sorts salaries from high to low → Emma, David, Bob, Carol, Alice
    
2. `OFFSET 1`: Skips **Emma (highest salary)**
    
3. `LIMIT 1`: Returns **David (second highest salary)**
    

---

##### ✅ Output:

|name|salary|
|---|---|
|David|8000|

---

##### ✅ Example 2: Get the 3rd highest salary

```sql
SELECT name, salary
FROM Employees
ORDER BY salary DESC
LIMIT 1 OFFSET 2;
```

🔸 Skips top 2 → Emma, David  
🔸 Returns the 3rd → **Bob**

---

##### ✅ Output:

|name|salary|
|---|---|
|Bob|7000|

---

#### 📝 Summary Table

|Clause|Description|Example|
|---|---|---|
|`LIMIT n`|Return **up to n rows**|`LIMIT 5`|
|`OFFSET m`|**Skip m rows** before starting to return|`OFFSET 2`|
|Combined|Skip m, then return next n|`LIMIT 3 OFFSET 2`|

---

#### ✅ Bonus: Pagination

```sql
-- Page 1: LIMIT 5 OFFSET 0
-- Page 2: LIMIT 5 OFFSET 5
-- Page 3: LIMIT 5 OFFSET 10
```

Useful for displaying data page by page in apps.

---

Would you like me to include a visual diagram or printable PDF for all these paging + OFFSET usages?
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


### `COALESCE()`
The `COALESCE()` function in SQL is used to **return the first non-NULL value** from a list of expressions.

---

#### 🔹 Syntax

```sql
COALESCE(value1, value2, ..., valueN)
```

- It checks values from left to right.
    
- It returns the **first value that is NOT NULL**.
    
- If **all values are NULL**, it returns `NULL`.
    

---

#### ✅ Example 1: Basic Usage

```sql
SELECT COALESCE(NULL, NULL, 'Hello', 'World');
```

🔹 **Output**:

```
Hello
```

🧠 Explanation: It returns `'Hello'` because it's the **first non-NULL** value.

---

#### ✅ Example 2: Handling NULL in Columns

Assume a `students` table:

|id|name|nickname|
|---|---|---|
|1|Alice|NULL|
|2|Bob|Bobby|
|3|Charlie|NULL|

You want to show the `nickname` if it exists, otherwise the `name`:

```sql
SELECT COALESCE(nickname, name) AS display_name
FROM students;
```

🔹 **Result**:

|display_name|
|---|
|Alice|
|Bobby|
|Charlie|

---

#### ✅ Example 3: With Default Values

If a `salary` is NULL, show `0` instead:

```sql
SELECT name, COALESCE(salary, 0) AS salary
FROM employees;
```

---

#### ✅ Example 4: With Multiple Fallbacks

```sql
SELECT COALESCE(NULL, NULL, NULL, 'Fallback', 'Other');
```

🔹 Returns: `'Fallback'`

---

#### 🔁 COALESCE vs ISNULL vs IFNULL

|Function|DB Systems Supported|Description|
|---|---|---|
|`COALESCE`|✅ ANSI SQL Standard|Returns first non-NULL from a list|
|`ISNULL(x, y)`|SQL Server only|Returns `x` if not NULL, else `y`|
|`IFNULL(x, y)`|MySQL only|Same as ISNULL|

---

#### 💡 Use Cases

|Use Case|Example|
|---|---|
|Replace NULL with default|`COALESCE(address, 'Not Provided')`|
|Prioritize multiple optional fields|`COALESCE(email, phone, 'No Contact Info')`|
|Avoid NULL in calculations|`price * COALESCE(discount, 1)`|

---

#### ⚠️ Notes

- All expressions in `COALESCE` should be of **compatible data types**.
    
- It stops evaluating as soon as it finds the **first non-NULL**.

# String Functions

## 📚 **Common SQL String Functions (with Examples)**

| Function                   | Description                                         | Example                        | Output     |
| -------------------------- | --------------------------------------------------- | ------------------------------ | ---------- |
| `CONCAT()`                 | Joins/combines two or more strings                  | `CONCAT('A', 'B')`             | `'AB'`     |
| `LEN()`                    | Returns length of string (**SQL Server**)           | `LEN('Hello')`                 | `5`        |
| `LENGTH()`                 | Returns length of string (**MySQL/PostgreSQL**)     | `LENGTH('Hello')`              | `5`        |
| `UPPER()`                  | Converts string to **uppercase**                    | `UPPER('hello')`               | `'HELLO'`  |
| `LOWER()`                  | Converts string to **lowercase**                    | `LOWER('HELLO')`               | `'hello'`  |
| `LEFT()`                   | Returns leftmost N characters                       | `LEFT('Hello', 2)`             | `'He'`     |
| `RIGHT()`                  | Returns rightmost N characters                      | `RIGHT('Hello', 3)`            | `'llo'`    |
| `SUBSTRING()` / `SUBSTR()` | Extracts part of a string from a position           | `SUBSTRING('Hello', 2, 3)`     | `'ell'`    |
| `REPLACE()`                | Replaces part of a string                           | `REPLACE('abcabc', 'a', 'x')`  | `'xbcxbc'` |
| `TRIM()`                   | Removes spaces (or characters) from both ends       | `TRIM(' Hello ')`              | `'Hello'`  |
| `LTRIM()`                  | Removes spaces from **left** side (**SQL Server**)  | `LTRIM(' Hello')`              | `'Hello'`  |
| `RTRIM()`                  | Removes spaces from **right** side (**SQL Server**) | `RTRIM('Hello ')`              | `'Hello'`  |
| `INSTR()`                  | Returns position of substring (**MySQL**)           | `INSTR('abcde', 'c')`          | `3`        |
| `POSITION()`               | Position of substring (**PostgreSQL**)              | `POSITION('c' IN 'abcde')`     | `3`        |
| `CHARINDEX()`              | Position of substring (**SQL Server**)              | `CHARINDEX('c', 'abcde')`      | `3`        |
| `REVERSE()`                | Reverses a string                                   | `REVERSE('abc')`               | `'cba'`    |
| `CONCAT_WS()`              | Concatenates with separator (**MySQL/PostgreSQL**)  | `CONCAT_WS('-', '2025', '07')` |            |
## ✅ 1. `CONCAT()` – Join Strings Together

### 🔹 Purpose:

Used to **combine two or more strings** into one.

### ✅ Syntax:

```sql
CONCAT(string1, string2, ..., stringN)
```

### ✅ Example:

```sql
SELECT CONCAT('Hello', ' ', 'World') AS result;
```

🔸 **Output:**

```
Hello World
```

---

### 📌 Real Table Example:

Assume a table `students`:

|first_name|last_name|
|---|---|
|Alice|Johnson|
|Bob|Smith|

```sql
SELECT CONCAT(first_name, ' ', last_name) AS full_name
FROM students;
```

🔸 **Result:**

|full_name|
|---|
|Alice Johnson|
|Bob Smith|

---

## ✅ 2. `LEN()` / `LENGTH()` – Get String Length

### 🔹 Purpose:

Returns the **number of characters** in a string.

> ✅ Note:
> 
> - `LEN()` is used in **SQL Server**
>     
> - `LENGTH()` is used in **MySQL, PostgreSQL, SQLite**
>     

### ✅ Syntax (SQL Server):

```sql
SELECT LEN('Hello') AS len;
```

🔸 Output:

```
5
```

### ✅ Syntax (MySQL, PostgreSQL):

```sql
SELECT LENGTH('Hello') AS len;
```

---

### 📌 Real Table Example:

```sql
SELECT name, LEN(name) AS name_length
FROM employees;
```

---

## ✅ 3. `UPPER()` – Convert to Uppercase

### 🔹 Purpose:

Converts **all characters** of a string to **uppercase**.

### ✅ Syntax:

```sql
SELECT UPPER('hello world') AS upper_text;
```

🔸 Output:

```
HELLO WORLD
```

---

### 📌 Real Table Example:

```sql
SELECT UPPER(first_name) AS upper_name
FROM students;
```

|first_name|upper_name|
|---|---|
|Alice|ALICE|
|Bob|BOB|

---

## ✅ 4. `LOWER()` – Convert to Lowercase

### 🔹 Purpose:

Converts **all characters** of a string to **lowercase**.

### ✅ Syntax:

```sql
SELECT LOWER('HELLO WORLD') AS lower_text;
```

🔸 Output:

```
hello world
```

---

### 📌 Real Table Example:

```sql
SELECT LOWER(email) AS clean_email
FROM users;
```

---

## ✅ 5. `LEFT()` – Get Leftmost Characters

### 🔹 Purpose:

Returns the **first N characters** from the **left** side of a string.

### ✅ Syntax:

```sql
SELECT LEFT('Database', 4) AS result;
```

🔸 **Output:**

```
Data
```

---

### 📌 Real Table Example:

Assume a table `employees`:

```sql
SELECT name, LEFT(name, 3) AS short_name
FROM employees;
```

🔸 **Result:**

|name|short_name|
|---|---|
|Prakash|Pra|
|Ananya|Ana|

---

## ✅ 6. `RIGHT()` – Get Rightmost Characters

### 🔹 Purpose:

Returns the **last N characters** from the **right** side of a string.

### ✅ Syntax:

```sql
SELECT RIGHT('Database', 4) AS result;
```

🔸 **Output:**

```
base
```

---

### 📌 Real Table Example:

```sql
SELECT name, RIGHT(name, 2) AS suffix
FROM employees;
```

|name|suffix|
|---|---|
|Prakash|sh|
|Ananya|ya|

---

## ✅ 7. `SUBSTRING()` / `SUBSTR()` – Extract Part of String

### 🔹 Purpose:

Extracts a **portion of a string** starting at a given position.

### ✅ Syntax:

```sql
SELECT SUBSTRING('Database', 2, 4) AS result;
```

- Start at position `2` (1-based index)
    
- Take `4` characters
    

🔸 **Output:**

```
ATAB
```

---

### 📌 Real Table Example:

```sql
SELECT email, SUBSTRING(email, 1, 5) AS prefix
FROM users;
```

|email|prefix|
|---|---|
|[prakash@gmail.com](mailto:prakash@gmail.com)|praka|

---

## ✅ 8. `REPLACE()` – Replace Substring

### 🔹 Purpose:

Replaces **part of a string** with something else.

### ✅ Syntax:

```sql
SELECT REPLACE('SQL is fun', 'fun', 'powerful') AS result;
```

🔸 **Output:**

```
SQL is powerful
```

---

### 📌 Real Table Example:

```sql
SELECT REPLACE(phone_number, '-', '') AS clean_number
FROM contacts;
```

|phone_number|clean_number|
|---|---|
|987-654-3210|9876543210|

---

## ✅ 9. `TRIM()` – Remove Spaces

### 🔹 Purpose:

Removes **leading and trailing spaces** (or specified characters) from a string.

### ✅ Syntax:

```sql
SELECT TRIM('   Hello   ') AS trimmed;
```

🔸 **Output:**

```
Hello
```

---

### 📌 Real Table Example:

```sql
SELECT TRIM(name) AS clean_name
FROM users;
```

---

## ✅ 10. `REVERSE()` – Reverse a String

### 🔹 Purpose:

Returns the **reverse** of the input string.

### ✅ Syntax:

```sql
SELECT REVERSE('SQL') AS reversed;
```

🔸 **Output:**

```
LQS
```

---

### 📌 Real Table Example:

```sql
SELECT name, REVERSE(name) AS flipped
FROM employees;
```

|name|flipped|
|---|---|
|Prakash|hsakarp|
|Ananya|ayanan|

---

| Function                   | Description                                         | Example                        | Output      |
| -------------------------- | --------------------------------------------------- | ------------------------------ | ----------- |
| `CONCAT()`                 | Joins/combines two or more strings                  | `CONCAT('A', 'B')`             | `'AB'`      |
| `LEN()`                    | Returns length of string (**SQL Server**)           | `LEN('Hello')`                 | `5`         |
| `LENGTH()`                 | Returns length of string (**MySQL/PostgreSQL**)     | `LENGTH('Hello')`              | `5`         |
| `UPPER()`                  | Converts string to **uppercase**                    | `UPPER('hello')`               | `'HELLO'`   |
| `LOWER()`                  | Converts string to **lowercase**                    | `LOWER('HELLO')`               | `'hello'`   |
| `LEFT()`                   | Returns leftmost N characters                       | `LEFT('Hello', 2)`             | `'He'`      |
| `RIGHT()`                  | Returns rightmost N characters                      | `RIGHT('Hello', 3)`            | `'llo'`     |
| `SUBSTRING()` / `SUBSTR()` | Extracts part of a string from a position           | `SUBSTRING('Hello', 2, 3)`     | `'ell'`     |
| `REPLACE()`                | Replaces part of a string                           | `REPLACE('abcabc', 'a', 'x')`  | `'xbcxbc'`  |
| `TRIM()`                   | Removes spaces (or characters) from both ends       | `TRIM(' Hello ')`              | `'Hello'`   |
| `LTRIM()`                  | Removes spaces from **left** side (**SQL Server**)  | `LTRIM(' Hello')`              | `'Hello'`   |
| `RTRIM()`                  | Removes spaces from **right** side (**SQL Server**) | `RTRIM('Hello ')`              | `'Hello'`   |
| `INSTR()`                  | Returns position of substring (**MySQL**)           | `INSTR('abcde', 'c')`          | `3`         |
| `POSITION()`               | Position of substring (**PostgreSQL**)              | `POSITION('c' IN 'abcde')`     | `3`         |
| `CHARINDEX()`              | Position of substring (**SQL Server**)              | `CHARINDEX('c', 'abcde')`      | `3`         |
| `REVERSE()`                | Reverses a string                                   | `REVERSE('abc')`               | `'cba'`     |
| `CONCAT_WS()`              | Concatenates with separator (**MySQL/PostgreSQL**)  | `CONCAT_WS('-', '2025', '07')` | `'2025-07'` |


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

## Aggregate Function

### ✅ What Are Aggregate Functions in SQL?

**Aggregate functions** perform a **calculation on a set of values** and return a **single summary value**.

They are often used with `GROUP BY` or in queries to get totals, averages, counts, etc.

---

### 🔸 Common Aggregate Functions

| Function  | Description                          |
| --------- | ------------------------------------ |
| `COUNT()` | Counts rows                          |
| `SUM()`   | Adds up numeric values               |
| `AVG()`   | Calculates average of numeric values |
| `MIN()`   | Finds the smallest (minimum) value   |
| `MAX()`   | Finds the largest (maximum) value    |

---

### 🔹 1. `COUNT()` – Count Rows

#### ✅ Example:

```sql
SELECT COUNT(*) FROM employees;
```

🔸 Counts **all rows** in the `employees` table.

---

#### ✅ With a condition:

```sql
SELECT COUNT(*) 
FROM employees 
WHERE department = 'Sales';
```

🔸 Counts only employees in the Sales department.

---

### 🔹 2. `SUM()` – Total of Column

#### ✅ Example:

```sql
SELECT SUM(salary) 
FROM employees;
```

🔸 Returns the total salary paid to all employees.

---

### 🔹 3. `AVG()` – Average Value

#### ✅ Example:

```sql
SELECT AVG(salary) 
FROM employees;
```

🔸 Gives the **average salary** of all employees.

---

### 🔹 4. `MIN()` and `MAX()` – Lowest & Highest

#### ✅ Example:

```sql
SELECT MIN(salary), MAX(salary) 
FROM employees;
```

🔸 Shows:

- The **lowest salary** in the company
    
- The **highest salary**
    

---

#### 🔸 Using `GROUP BY` with Aggregate Functions

You can use `GROUP BY` to get aggregate values **per group**.

#### 🧾 Example Table: `employees`

|id|name|department|salary|
|---|---|---|---|
|1|Alice|HR|30000|
|2|Bob|IT|50000|
|3|Jane|HR|35000|
|4|Mark|IT|60000|

---

#### ✅ Query: Average Salary Per Department

```sql
SELECT department, AVG(salary)
FROM employees
GROUP BY department;
```

🔸 Output:

|department|avg(salary)|
|---|---|
|HR|32500|
|IT|55000|

---

### 🔸 Filtering Aggregates with `HAVING`

Use `HAVING` to filter **after aggregation** (not `WHERE`).

#### ✅ Query: Departments with average salary > 40000

```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 40000;
```

---

### ✅ Summary Table

| Function  | Purpose           | Example                       |
| --------- | ----------------- | ----------------------------- |
| `COUNT()` | Count rows        | `COUNT(*)` or `COUNT(column)` |
| `SUM()`   | Add values        | `SUM(price)`                  |
| `AVG()`   | Average of values | `AVG(score)`                  |
| `MIN()`   | Smallest value    | `MIN(age)`                    |
| `MAX()`   | Largest value     | `MAX(salary)`                 |

---

### 🧠 Notes

- `COUNT(*)` counts **all rows**, even if there are NULLs.
    
- `COUNT(column)` ignores **NULL values**.
    
- `AVG()`, `SUM()` work only on numeric data.
    
- Combine with `GROUP BY` to get per-group summaries.
    
- Use `HAVING` to filter groups **after aggregation**.
    

---


## GROUP BY – What is it?

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

## **** Aggregate function ** 
#### ✅ What Are Aggregate Functions in SQL?

**Aggregate functions** perform a **calculation on a set of values** and return a **single summary value**.

They are often used with `GROUP BY` or in queries to get totals, averages, counts, etc.

---

#### 🔸 Common Aggregate Functions

|Function|Description|
|---|---|
|`COUNT()`|Counts rows|
|`SUM()`|Adds up numeric values|
|`AVG()`|Calculates average of numeric values|
|`MIN()`|Finds the smallest (minimum) value|
|`MAX()`|Finds the largest (maximum) value|

---

#### 🔹 1. `COUNT()` – Count Rows

##### ✅ Example:

sql

CopyEdit

`SELECT COUNT(*) FROM employees;`

🔸 Counts **all rows** in the `employees` table.

---

##### ✅ With a condition:

sql

CopyEdit

`SELECT COUNT(*)  FROM employees  WHERE department = 'Sales';`

🔸 Counts only employees in the Sales department.

---

#### 🔹 2. `SUM()` – Total of Column

##### Example:

sql

CopyEdit

`SELECT SUM(salary)  FROM employees;`

🔸 Returns the total salary paid to all employees.

---

#### 🔹 3. `AVG()` – Average Value

##### ✅ Example:

sql

CopyEdit

`SELECT AVG(salary)  FROM employees;`

🔸 Gives the **average salary** of all employees.

---

#### 🔹 4. `MIN()` and `MAX()` – Lowest & Highest

##### Example:

sql

CopyEdit

`SELECT MIN(salary), MAX(salary)  FROM employees;`

🔸 Shows:

- The **lowest salary** in the company
    
- The **highest salary**
    

---

#### 🔹 5.`GROUP_CONCAT()` – Combine Grouped Values into a String

##### **Purpose**:

`GROUP_CONCAT()` is an **aggregate function** in MySQL used to **combine multiple rows into a single string**, separated by a comma (or custom delimiter).

---

##### Syntax:

```sql
GROUP_CONCAT([DISTINCT] column_name
             [ORDER BY col ASC|DESC]
             [SEPARATOR 'separator'])
```

---

##### 📘 Example Table: `students`

|class|student_name|
|---|---|
|A|Alice|
|A|Bob|
|B|Charlie|
|B|David|

---

##### ✅ Example 1: Basic Group Concatenation

```sql
SELECT class,
       GROUP_CONCAT(student_name) AS students
FROM students
GROUP BY class;
```

###### 🔹 Output:

|class|students|
|---|---|
|A|Alice,Bob|
|B|Charlie,David|

---

##### ✅ Example 2: With `ORDER BY` Inside

```sql
SELECT class,
       GROUP_CONCAT(student_name ORDER BY student_name DESC) AS students
FROM students
GROUP BY class;
```

🔸 Orders names descending inside each group.

---

##### ✅ Example 3: With Custom Separator

```sql
SELECT class,
       GROUP_CONCAT(student_name SEPARATOR ' | ') AS students
FROM students
GROUP BY class;
```

🔸 Output:

|class|students|
|---|---|
|A|Alice|
|B|Charlie|

---

##### ✅ Example 4: With `DISTINCT` to avoid duplicates

```sql
SELECT class,
       GROUP_CONCAT(DISTINCT student_name) AS students
FROM students
GROUP BY class;
```

🔸 Removes duplicate names in the group.

---

##### 🧠 Notes:

- `GROUP_CONCAT()` is **MySQL-specific** (not supported in SQL Server or PostgreSQL directly).
    
- Default separator is `,`.
    
- You can **limit result length** using:
    
    ```sql
    SET SESSION group_concat_max_len = 100000;
    ```
    

---

##### ✅ Summary Table:

| Feature              | Usage Example                                |
| -------------------- | -------------------------------------------- |
| Basic use            | `GROUP_CONCAT(name)`                         |
| With sort            | `GROUP_CONCAT(name ORDER BY name DESC)`      |
| Custom separator     | `GROUP_CONCAT(name SEPARATOR '               |
| Remove duplicates    | `GROUP_CONCAT(DISTINCT name)`                |
| Set max length limit | `SET SESSION group_concat_max_len = 100000;` |

---
#### 🔸 Using `GROUP BY` with Aggregate Functions

You can use `GROUP BY` to get aggregate values **per group**.

#### 🧾 Example Table: `employees`

|id|name|department|salary|
|---|---|---|---|
|1|Alice|HR|30000|
|2|Bob|IT|50000|
|3|Jane|HR|35000|
|4|Mark|IT|60000|

---

#### ✅ Query: Average Salary Per Department

sql

CopyEdit

`SELECT department, AVG(salary) FROM employees GROUP BY department;`

🔸 Output:

|department|avg(salary)|
|---|---|
|HR|32500|
|IT|55000|

---

#### 🔸 Filtering Aggregates with `HAVING`

Use `HAVING` to filter **after aggregation** (not `WHERE`).

#### ✅ Query: Departments with average salary > 40000

sql

CopyEdit

`SELECT department, AVG(salary) AS avg_salary FROM employees GROUP BY department HAVING AVG(salary) > 40000;`

---

#### ✅ Summary Table

|Function|Purpose|Example|
|---|---|---|
|`COUNT()`|Count rows|`COUNT(*)` or `COUNT(column)`|
|`SUM()`|Add values|`SUM(price)`|
|`AVG()`|Average of values|`AVG(score)`|
|`MIN()`|Smallest value|`MIN(age)`|
|`MAX()`|Largest value|`MAX(salary)`|

---

#### 🧠 Notes

- `COUNT(*)` counts **all rows**, even if there are NULLs.
    
- `COUNT(column)` ignores **NULL values**.
    
- `AVG()`, `SUM()` work only on numeric data.
    
- Combine with `GROUP BY` to get per-group summaries.
    
- Use `HAVING` to filter groups **after aggregation**.
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
##  **What is a Subquery?**

A **subquery** (also called an **inner query** or **nested query**) is a query **inside another query**.  
It's used when you want to get data from one query and **use it inside another**.

---

# ✅ **1. Basic Subquery (in WHERE clause)**

### 🧠 Use Case:

To **filter data** based on a result from another query.

### 🗂️ Example Tables:

**Employees**

|id|name|department_id|
|---|---|---|
|1|Alice|1|
|2|Bob|2|
|3|Charlie|1|

**Departments**

|id|dept_name|
|---|---|
|1|HR|
|2|Engineering|

---

### 📌 Example Query:

Find employees who work in the **HR** department.

```sql
SELECT name
FROM Employees
WHERE department_id = (
    SELECT id
    FROM Departments
    WHERE dept_name = 'HR'
);
```

✅ Here, the **subquery** returns `1` (id of HR), and the outer query selects employees with `department_id = 1`.

---

# ✅ **2. Subquery in SELECT Clause**

### 🧠 Use Case:

To add a **calculated column** using another query.

### 📌 Example Query:

Show each employee's name and their department name.

```sql
SELECT name,
    (SELECT dept_name 
     FROM Departments 
     WHERE Departments.id = Employees.department_id) AS dept_name
FROM Employees;
```

✅ The subquery runs **for each row** in Employees.

---

# ✅ **3. Subquery in FROM Clause** (Derived Table / Inline View)

### 🧠 Use Case:

Use a subquery as a **temporary table**.

### 📌 Example Query:

Get the number of employees in each department.

```sql
SELECT dept_name, COUNT(*) AS total_employees
FROM (
    SELECT e.id, d.dept_name
    FROM Employees e
    JOIN Departments d ON e.department_id = d.id
) AS dept_employees
GROUP BY dept_name;
```

✅ The subquery (`dept_employees`) returns a combined table with employee and department names, which is then grouped.

---

# ✅ **4. Correlated Subquery**

### 🧠 Use Case:

A subquery that **depends on each row** from the outer query.

### 📌 Example Query:

Get employees whose department has more than 1 employee.

```sql
SELECT name
FROM Employees e1
WHERE (
    SELECT COUNT(*) 
    FROM Employees e2 
    WHERE e2.department_id = e1.department_id
) > 1;
```

✅ The subquery is **correlated** with the outer query — it runs for each employee.

---

# ✅ **5. EXISTS with Subquery**

### 🧠 Use Case:

Check if **a row exists** in another table.

### 📌 Example Query:

Get departments that have employees.

```sql
SELECT dept_name
FROM Departments d
WHERE EXISTS (
    SELECT 1
    FROM Employees e
    WHERE e.department_id = d.id
);
```

✅ The subquery checks whether **at least one employee** is in that department.

---

# ✅ **6. NOT EXISTS Subquery**

### 📌 Example Query:

Get departments with **no employees**.

```sql
SELECT dept_name
FROM Departments d
WHERE NOT EXISTS (
    SELECT 1
    FROM Employees e
    WHERE e.department_id = d.id
);
```

✅ Subquery returns false if any employee exists in that department.

---

# ✅ **7. IN vs EXISTS vs JOIN**

- `IN` is simple, but can be slower with large subquery result sets.
    
- `EXISTS` is usually faster when subquery returns **a lot of rows**.
    
- `JOIN` is better if you want to **return data from both tables**.
    

---

# ✅ **8. Subquery with Aggregates**

### 📌 Example Query:

Get employees who earn **more than the average salary**.

```sql
SELECT name, salary
FROM Employees
WHERE salary > (
    SELECT AVG(salary) FROM Employees
);
```

✅ Subquery calculates average salary, outer query compares it.

---

# ✅ **9. Nested Subqueries**

### 📌 Example:

Find employees in the **department with the highest total salary**.

```sql
SELECT name
FROM Employees
WHERE department_id = (
    SELECT department_id
    FROM Employees
    GROUP BY department_id
    ORDER BY SUM(salary) DESC
    LIMIT 1
);
```

✅ Inner subquery finds the `department_id` with max salary sum.

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

### **🔹 Key Takeaways**

### **📌 Subquery in `FROM` (Derived Table)**

✔ The **subquery acts as a temporary table**.  
✔ Useful when you need to **precompute** something and use it in the main query.

### **📌 Subquery in `HAVING` (Filtering Groups)**

✔ `HAVING` is used **after `GROUP BY`** to filter grouped results.  
✔ `HAVING AVG(salary) > (SELECT AVG(salary))` **compares each department’s average salary to the overall average**.

---

### **🔹 Summary Table**

|**Type**|**When to Use?**|**Example Use Case**|
|---|---|---|
|**Subquery in `FROM`**|When you need to **create a temporary table** for further filtering|Find **average salary per department**|
|**Subquery in `HAVING`**|When you need to **filter groups** based on a condition|Find **departments where the avg salary is above the global avg**|

Would you like more examples or clarification on any part? 🚀
### **🔹 Key Takeaways**

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


### 🚀 Summary Table

|Subquery Type|Where Used?|Key Use Case|
|---|---|---|
|Basic Subquery|WHERE clause|Filtering using another query|
|Subquery in SELECT|SELECT clause|Adding extra info/column|
|Subquery in FROM|FROM clause|Treat as temporary/virtual table|
|Correlated Subquery|WHERE/SELECT|Subquery depends on outer query|
|EXISTS / NOT EXISTS|WHERE clause|Check if rows exist or not|
|Nested Subqueries|Anywhere|Layered logic (complex scenarios)|
### [[SQL Exercises.pdf]](SubQuery Excercises)

---



# Numeric & Math Functions in SQL**

### 🔢 **1.1 `RAND()`**

- **Purpose**: Returns a random floating-point number between **0 (inclusive)** and **1 (exclusive)**.
    
- **Syntax**: `RAND([seed])`
    
    - `seed` is optional and gives the same result every time when provided.
        
- **Example**:
    
    ```sql
    SELECT RAND();         -- Example output: 0.726481
    SELECT RAND(10);       -- Always returns the same value for seed 10
    ```
    

---

### 🔁 **1.2 `ROUND()`**

- **Purpose**: Rounds a number to a specified number of decimal places.
    
- **Syntax**: `ROUND(number, decimal_places)`
    
- **Example**:
    
    ```sql
    SELECT ROUND(123.4567, 2);   -- Output: 123.46
    SELECT ROUND(123.4567, 0);   -- Output: 123
    ```
    

---

### ⬇️ **1.3 `FLOOR()`**

- **Purpose**: Returns the largest integer **less than or equal to** the number.
    
- **Syntax**: `FLOOR(number)`
    
- **Example**:
    
    ```sql
    SELECT FLOOR(123.9);    -- Output: 123
    SELECT FLOOR(-123.9);   -- Output: -124
    ```
    

---

### ⬆️ **1.4 `CEIL()` or `CEILING()`**

- **Purpose**: Returns the smallest integer **greater than or equal to** the number.
    
- **Syntax**: `CEIL(number)` or `CEILING(number)`
    
- **Example**:
    
    ```sql
    SELECT CEIL(123.1);     -- Output: 124
    SELECT CEIL(-123.1);    -- Output: -123
    ```
    

---

### ➕➖ **1.5 `ABS()`**

- **Purpose**: Returns the absolute (positive) value of a number.
    
- **Syntax**: `ABS(number)`
    
- **Example**:
    
    ```sql
    SELECT ABS(-25);        -- Output: 25
    SELECT ABS(25);         -- Output: 25
    ```
    

---

### 🔋 **1.6 `POWER()`**

- **Purpose**: Raises a number to the power of another number (exponent).
    
- **Syntax**: `POWER(base, exponent)`
    
- **Example**:
    
    ```sql
    SELECT POWER(2, 3);     -- Output: 8 (2³)
    SELECT POWER(5, 2);     -- Output: 25
    ```
    

---

### 🧮 **1.7 `SQRT()`**

- **Purpose**: Returns the square root of a number.
    
- **Syntax**: `SQRT(number)`
    
- **Example**:
    
    ```sql
    SELECT SQRT(25);        -- Output: 5
    SELECT SQRT(2);         -- Output: 1.4142...
    ```
    

---

## ✅ Summary Table

|Function|Description|Example|Result|
|---|---|---|---|
|`RAND()`|Random float between 0 and 1|`RAND()`|0.726|
|`ROUND()`|Round number to N decimals|`ROUND(123.456, 2)`|123.46|
|`FLOOR()`|Round **down** to nearest integer|`FLOOR(123.9)`|123|
|`CEIL()`|Round **up** to nearest integer|`CEIL(123.1)`|124|
|`ABS()`|Absolute value (removes negative sign)|`ABS(-5)`|5|
|`POWER()`|Raise number to a power|`POWER(3, 2)`|9|
|`SQRT()`|Square root|`SQRT(16)`|4|

---

## 📘 Bonus Tips for Preparation

- Use `SELECT` statements to practice these in an SQL tool (like MySQL, PostgreSQL, or SQLite).
    
- Combine functions:
    
    ```sql
    SELECT ROUND(SQRT(20), 2);  -- Output: 4.47
    ```
    
- Try real data columns:
    
    ```sql
    SELECT name, ROUND(salary, 0), FLOOR(salary), CEIL(salary) FROM employees;
    ```
    

---

Would you like some **practice problems** for each of these functions?
# **Window Function**
## ✅ What Is a Window Function?

A **window function** performs a **calculation across a set of table rows that are somehow related to the current row**, without collapsing the rows like `GROUP BY` does.

🔹 It **does not group or reduce** the number of rows — instead, it returns a **value for each row** based on a **"window" (a subset of rows)**.

---

## 🧠 Syntax of Window Function
```sql
<function_name>() OVER (
    [PARTITION BY column]
    [ORDER BY column]
    [ROWS ...]
)
```

This is how **window functions** work in SQL — they allow you to compute values across a "window" (a subset of rows related to the current row) without collapsing the result like `GROUP BY` does.

---

## 🧱 Full Breakdown of Each Part:

---
• expression|column: The target column for which the window function will compute a
value.
• OVER() clause: Defines the window or set of rows on which the window function
operates. Without this clause, the function operates on all rows in the result set.
• PARTITION BY (Optional): Divides the result set into partitions or sets, and the window
function is applied to each partition separately. It works similarly to GROUP BY, but it
doesn't reduce the number of rows.

◦ SUM(salary) OVER (PARTITION BY department)

• ORDER BY (Optional): Specifies the order in which rows are processed within each
partition. Useful for ranking or time-based calculations.
### ✅ 1. `<function_name>()`

This is the **window function** you're using. Some common ones are:

| Function          | What it does                                    |
| ----------------- | ----------------------------------------------- |
| `ROW_NUMBER()`    | Gives a unique row number within a partition    |
| `RANK()`          | Gives a rank with gaps if values are equal      |
| `DENSE_RANK()`    | Like `RANK()` but no gaps                       |
| `SUM(column)`     | Running total (cumulative sum)                  |
| `AVG(column)`     | Running average                                 |
| `LAG(column, n)`  | Gets value from `n` rows before the current one |
| `LEAD(column, n)` | Gets value from `n` rows after the current one  |

---

### ✅ 2. `OVER (...)`

This clause **defines the "window"** — i.e., the set of rows the function will operate over. Inside it, you can use:

---

### ✅ 3. `PARTITION BY column`

- Divides the data into groups (like `GROUP BY`) **within the window function**.
    
- The function restarts for each partition.
    

#### 💡 Example:

```sql
ROW_NUMBER() OVER (PARTITION BY department_id ORDER BY salary DESC)
```

This will:

- Assign a row number **starting from 1** for each `department_id`
    
- Ordered by `salary DESC` within each department
    

---

### ✅ 4. `ORDER BY column`

- Specifies the **order of rows** within each partition for the function to work on.
    

#### Example with `LAG()`:

```sql
LAG(salary) OVER (PARTITION BY department_id ORDER BY hire_date)
```

- For each department, get the salary of the person who was hired **just before** the current person.
    

---

### ✅ 5. `ROWS BETWEEN ...`

This is **optional** and defines an **explicit window frame**.

Used with aggregate functions like `SUM()` or `AVG()` to limit rows in the window:

#### Example:

```sql
SUM(salary) OVER (ORDER BY hire_date ROWS BETWEEN 2 PRECEDING AND CURRENT ROW)
```

This gives a sum of:

- The current row
    
- The 2 rows before it (based on `hire_date`)
    

#### Common Frame Options:

|Syntax|Meaning|
|---|---|
|`ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW`|From the first row up to the current one (running total)|
|`ROWS BETWEEN 1 PRECEDING AND 1 FOLLOWING`|One before, current, and one after|
|`ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING`|From current row to the end|

---

## 🧩 Full Example

```sql
SELECT 
    employee_id,
    department_id,
    salary,
    RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS dept_rank,
    SUM(salary) OVER (PARTITION BY department_id ORDER BY salary ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS running_total
FROM Employee;
```

### 🔍 What it does:

- `RANK()` gives each employee a rank within their department based on salary
    
- `SUM()` gives a **cumulative total** of salaries **within their department**
    

---

## ✅ Summary Table

|Clause|What it does|
|---|---|
|`OVER`|Defines the window for the function|
|`PARTITION BY`|Resets the function per group (like `GROUP BY` inside window)|
|`ORDER BY`|Sets the order in which the function is applied|
|`ROWS BETWEEN ...`|Defines a specific range of rows (optional, mainly for aggregates)|

---

Would you like a visual diagram or to practice this with real datasets like sales, salaries, or student marks?

## 📌 Most Common Window Functions

|Function|Purpose|
|---|---|
|`ROW_NUMBER()`|Assigns a unique row number|
|`RANK()`|Gives rank with gaps|
|`DENSE_RANK()`|Gives rank without gaps|
|`NTILE(N)`|Divides rows into N equal groups|
|`SUM()`|Running or partitioned sum|
|`AVG()`|Running or partitioned average|
|`LEAD()`|Get next row’s value|
|`LAG()`|Get previous row’s value|

---

## 🎯 Sample Table: `sales`

Imagine we have this table:

| id | employee | department | sales |
| -- | -------- | ---------- | ----- |
| 1  | Alice    | A          | 500   |
| 2  | Bob      | A          | 300   |
| 3  | Carol    | B          | 800   |
| 4  | Dave     | A          | 700   |
| 5  | Erin     | B          | 600   |

---

## 🔸 1. `ROW_NUMBER()` – Unique number per row (per group)

```sql
SELECT employee, department, sales,
  ROW_NUMBER() OVER (PARTITION BY department ORDER BY sales DESC) AS row_num
FROM sales;
```

📌 This assigns a **unique number** starting from 1 **within each department**, based on `sales DESC`.

### 🧾 Output:

| employee | department | sales | row\_num |
| -------- | ---------- | ----- | -------- |
| Dave     | A          | 700   | 1        |
| Alice    | A          | 500   | 2        |
| Bob      | A          | 300   | 3        |
| Carol    | B          | 800   | 1        |
| Erin     | B          | 600   | 2        |

---

### What are `RANK()` and `DENSE_RANK()`?

Both are **window functions** used to assign a rank to each row within a partition of a result set based on a specific column order (typically used with `ORDER BY` inside `OVER()`).

- **`RANK()`**: Gives **gaps** in ranking when there are ties.
    
- **`DENSE_RANK()`**: Gives **no gaps**—ranks increase consecutively even if there are ties.
    

---

### 🔸 Example Table: `Sales`

|Employee|Region|Sales|
|---|---|---|
|Alice|East|1000|
|Bob|East|900|
|Carol|East|900|
|Dave|East|800|
|Eve|West|950|
|Frank|West|950|
|Grace|West|900|

---

### 🔹 SQL Query with `RANK()` and `DENSE_RANK()`

sql

CopyEdit

`SELECT      Employee,     Region,     Sales,     RANK() OVER (PARTITION BY Region ORDER BY Sales DESC) AS rank_pos,     DENSE_RANK() OVER (PARTITION BY Region ORDER BY Sales DESC) AS dense_rank_pos FROM Sales;`

---

### 🔸 Output Explained

|Employee|Region|Sales|RANK()|DENSE_RANK()|
|---|---|---|---|---|
|Alice|East|1000|1|1|
|Bob|East|900|2|2|
|Carol|East|900|2|2|
|Dave|East|800|4|3|
|Eve|West|950|1|1|
|Frank|West|950|1|1|
|Grace|West|900|3|2|

---

### ✅ Key Differences:

- In the **East region**, Bob and Carol tie with 900 sales:
    
    - `RANK()` assigns both a **2**, but the next rank is **4** (skips 3).
        
    - `DENSE_RANK()` assigns both a **2**, and the next rank is **3** (no gap).
        
- In the **West region**, Eve and Frank tie with 950 sales:
    
    - `RANK()` assigns both a **1**, next is **3** (Grace).
        
    - `DENSE_RANK()` assigns both a **1**, next is **2**.
        

---

### 🔹 When to Use Which?

- Use **`RANK()`** if you want to reflect the true **position including ties** (with skipped ranks).
    
- Use **`DENSE_RANK()`** if you want to **avoid gaps** in ranking.
## 🔸 4. `SUM()` – Running total (cumulative)

```sql
SELECT employee, department, sales,
  SUM(sales) OVER (PARTITION BY department ORDER BY sales) AS running_total
FROM sales;
```

📌 For each department, it adds up the sales **up to the current row** (running total).

### 🧾 Output:

| employee | dept | sales | running\_total |
| -------- | ---- | ----- | -------------- |
| Bob      | A    | 300   | 300            |
| Alice    | A    | 500   | 800            |
| Dave     | A    | 700   | 1500           |
| Erin     | B    | 600   | 600            |
| Carol    | B    | 800   | 1400           |

---

## 🔸 5. `LAG()` – Previous row’s value
Syntax:
----------------------------------------------------------------
```sql
LAG(column_name, offset, default_value)
OVER ( [ PARTITION BY expr_list optional ]
ORDER BY order_list )
```
 column_name: The column from which to fetch the value.
 offset: Number of rows behind from the current row (default is 1).
 default_value: Value to return if the offset goes beyond the dataset (optional).
```sql
SELECT employee, department, sales,
  LAG(sales) OVER (PARTITION BY department ORDER BY sales) AS previous_sales
FROM sales;
```

📌 Shows the `sales` value of the **previous row** in each department group.

### 🧾 Output:

| employee | dept | sales | previous\_sales |
| -------- | ---- | ----- | --------------- |
| Bob      | A    | 300   | NULL            |
| Alice    | A    | 500   | 300             |
| Dave     | A    | 700   | 500             |
| Erin     | B    | 600   | NULL            |
| Carol    | B    | 800   | 600             |

---

## 🔸 6. `LEAD()` – Next row’s value
Syntax:
----------------------------------------------------------------
```sql
LEAD(column_name, offset, default_value)
OVER ( [ PARTITION BY expr_list optional ]
ORDER BY order_list )
```
 column_name: The column from which to fetch the value.
 offset: Number of rows ahead from the current row (default is 1).
 default_value: Value to return if the offset goes beyond the dataset (optional).
```sql
SELECT employee, department, sales,
  LEAD(sales) OVER (PARTITION BY department ORDER BY sales) AS next_sales
FROM sales;
```

📌 Shows the `sales` value of the **next row** in each department group.

### 🧾 Output:

| employee | dept | sales | next\_sales |
| -------- | ---- | ----- | ----------- |
| Bob      | A    | 300   | 500         |
| Alice    | A    | 500   | 700         |
| Dave     | A    | 700   | NULL        |
| Erin     | B    | 600   | 800         |
| Carol    | B    | 800   | NULL        |

---

## 🔸 7. `NTILE(n)` – Split rows into buckets

```sql
SELECT employee, department, sales,
  NTILE(2) OVER (ORDER BY sales DESC) AS bucket
FROM sales;
```

📌 Divides the entire result set into **2 groups** (as evenly as possible).

### 🧾 Output:

| employee | sales | bucket |
| -------- | ----- | ------ |
| Carol    | 800   | 1      |
| Dave     | 700   | 1      |
| Erin     | 600   | 1      |
| Alice    | 500   | 2      |
| Bob      | 300   | 2      |

---

## ✅ Summary of Window Functions

| Function       | Purpose                       |
| -------------- | ----------------------------- |
| `ROW_NUMBER()` | Unique row number per group   |
| `RANK()`       | Rank with gaps                |
| `DENSE_RANK()` | Rank without gaps             |
| `SUM()`        | Running or grouped totals     |
| `LAG()`        | Get value from previous row   |
| `LEAD()`       | Get value from next row       |
| `NTILE(n)`     | Distribute rows into n groups |
|                |                               |
***Nth_VALUE(),FIRST_VALUE() and LAST_VALUE() are in below pdf
### [[WINDOW FUNCTIONS GUIDE.pdf]]
---

## 🔰 What is a CTE?

A **Common Table Expression (CTE)** is a temporary result set you can reference within a `SELECT`, `INSERT`, `UPDATE`, or `DELETE` query.

Think of it like creating a **temporary named result** (like a virtual table) to make your query easier to read, debug, and reuse.

---

## 🧱 Basic Syntax

```sql
WITH cte_name AS (
    SELECT ...
    FROM ...
    WHERE ...
)
SELECT * FROM cte_name;
```

---

## 🪜 Step-by-Step Breakdown

### ✅ Step 1: Traditional Approach Without CTE

```sql
SELECT department_id
FROM (
    SELECT department_id, COUNT(*) as emp_count
    FROM Employee
    GROUP BY department_id
) AS temp
WHERE emp_count > 5;
```

This is harder to read when nested multiple times.

---

### ✅ Step 2: With CTE (Same logic, cleaner)

```sql
WITH DepartmentCount AS (
    SELECT department_id, COUNT(*) AS emp_count
    FROM Employee
    GROUP BY department_id
)
SELECT department_id
FROM DepartmentCount
WHERE emp_count > 5;
```

📌 `DepartmentCount` is the CTE name — it's like a temporary view we can query from.

---

## 🛠️ Key Benefits of Using CTE

|Feature|Benefit|
|---|---|
|Readability|Simplifies complex queries with nested subqueries|
|Reusability|You can refer to the same logic multiple times|
|Recursion (advanced)|You can perform recursive operations using CTEs|
|Modular design|Break logic into steps (like declaring variables)|

---

## 🧠 Multiple CTEs

```sql
WITH dept_count AS (
    SELECT department_id, COUNT(*) AS emp_count
    FROM Employee
    GROUP BY department_id
),
high_load_depts AS (
    SELECT department_id
    FROM dept_count
    WHERE emp_count > 5
)
SELECT e.employee_id, e.department_id
FROM Employee e
JOIN high_load_depts h ON e.department_id = h.department_id;
```

✔️ We created 2 CTEs and used them like intermediate steps.

---

## 🔄 Recursive CTE (Advanced)

Used to solve problems like hierarchy, path-finding, trees, etc.

### 🎯 Example: Employee Manager Chain

Table:

```sql
Employee(employee_id, name, manager_id)
```

### Query: Show management chain

```sql
WITH RECURSIVE ManagementChain AS (
    SELECT employee_id, name, manager_id, 1 AS level
    FROM Employee
    WHERE manager_id IS NULL  -- CEO level
    
    UNION ALL

    SELECT e.employee_id, e.name, e.manager_id, mc.level + 1
    FROM Employee e
    JOIN ManagementChain mc ON e.manager_id = mc.employee_id
)
SELECT * FROM ManagementChain;
```

This recursively follows the reporting hierarchy.

---

## 🧪 Real Example: LeetCode Style

Given:

```sql
Employee(employee_id, department_id, primary_flag)
```

CTE to get department counts:

```sql
WITH DeptCount AS (
    SELECT employee_id, COUNT(*) AS dept_count
    FROM Employee
    GROUP BY employee_id
)
SELECT e.employee_id, e.department_id
FROM Employee e
JOIN DeptCount d ON e.employee_id = d.employee_id
WHERE e.primary_flag = 'Y' OR d.dept_count = 1;
```

---

## 🔐 CTE vs TEMP TABLE vs SUBQUERY

|Feature|CTE|Temp Table|Subquery|
|---|---|---|---|
|Scope|One query|Session (can persist)|One-time use|
|Readability|High|Moderate|Low (nested)|
|Reusability|Within query|Across queries (temp)|Not reusable|
|Performance|Similar, but not indexed|Can be indexed|Inline only|

---

## 🧩 Summary

|Concept|Description|
|---|---|
|CTE|A temporary named result set inside a SQL query|
|Syntax|`WITH name AS (SELECT ...)`|
|Recursive CTE|Allows self-referencing for tree or hierarchy logic|
|Multiple CTEs|Can be declared in sequence with commas|
|Best for|Clean, readable queries; replacing subqueries|
|Not for|Long-term storage or indexed operations (use temp tables for that)|

---

Would you like practice questions or use CTEs in specific real-world scenarios (e.g., top N per group, salary hierarchy, etc.)?
#### [[Advanced SQL.pdf]]
### [[🚀 Top 10 Complex SQL Queries You Must Know! 🛠️___.pdf]]
# Frequently Asked Questions

**What is SQL used for?**

SQL is used for managing and manipulating data in relational database management systems (RDBMS). It allows users to query, update, and delete data from databases.

**What are the main components of an SQL statement?**

An SQL statement typically consists of clauses like SELECT, FROM, WHERE, and may also include keywords like JOIN, GROUP BY, and ORDER BY, depending on the specific operation.

**What's the difference between SQL and MySQL?**

SQL is a language for managing databases, while MySQL is a specific database management system that uses SQL as its query language. MySQL is just one of many RDBMS options available.

**What are the different types of SQL statements?**

SQL statements can broadly be categorized into Data Manipulation Language (DML) statements (e.g., SELECT, INSERT, UPDATE, DELETE), Data Definition Language (DDL) statements (e.g., CREATE, ALTER, DROP), and Data Control Language (DCL) statements (e.g., GRANT, REVOKE).

**What are primary keys and foreign keys in SQL?**

A primary key is an unique identifier for a record in a table, ensuring each row has a distinct identity. A foreign key, on the other hand, establishes a link between tables, typically referencing the primary key of another table.

**What is a SQL JOIN, and how does it work?**

SQL JOIN is used to combine rows from two or more tables based on a related column between them. Common joins include INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL OUTER JOIN.

**What are SQL transactions and why are they significant?**

SQL transactions are sequences of one or more SQL statements treated as a single unit of work. They are important for ensuring data consistency and integrity, allowing you to make multiple changes to a database as a single operation.