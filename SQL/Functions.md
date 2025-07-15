In MySQL, several **date and time functions** allow manipulation of dates like `DATE_SUB` and `INTERVAL`. Below is a list of similar functions:

---

### **1. Date Arithmetic Functions**

|Function|Description|Example|
|---|---|---|
|`DATE_ADD(date, INTERVAL value unit)`|Adds a specific interval to a date|`DATE_ADD('2024-03-01', INTERVAL 5 DAY)` → `'2024-03-06'`|
|`DATE_SUB(date, INTERVAL value unit)`|Subtracts a specific interval from a date|`DATE_SUB('2024-03-01', INTERVAL 5 DAY)` → `'2024-02-25'`|
|`ADDDATE(date, INTERVAL value unit)`|Same as `DATE_ADD`|`ADDDATE('2024-03-01', INTERVAL 2 MONTH)` → `'2024-05-01'`|
|`SUBDATE(date, INTERVAL value unit)`|Same as `DATE_SUB`|`SUBDATE('2024-03-01', INTERVAL 10 DAY)` → `'2024-02-20'`|

---

### **2. Date Difference & Extraction**

| Function                            | Description                                  | Example                                                                   |
| ----------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------- |
| `DATEDIFF(date1, date2)`            | Returns the number of days between two dates | `DATEDIFF('2024-03-10', '2024-03-01')` → `9`                              |
| `TIMESTAMPDIFF(unit, date1, date2)` | Returns difference in specified unit         | `TIMESTAMPDIFF(HOUR, '2024-03-01 08:00:00', '2024-03-01 10:00:00')` → `2` |
| `YEAR(date)`                        | Extracts the year from a date                | `YEAR('2024-03-01')` → `2024`                                             |
| `MONTH(date)`                       | Extracts the month from a date               | `MONTH('2024-03-01')` → `3`                                               |
| `DAY(date)`                         | Extracts the day from a date                 | `DAY('2024-03-01')` → `1`                                                 |
| `HOUR(time)`                        | Extracts the hour from a time                | `HOUR('10:30:00')` → `10`                                                 |
| `MINUTE(time)`                      | Extracts the minutes from a time             | `MINUTE('10:30:00')` → `30`                                               |
| `SECOND(time)`                      | Extracts the seconds from a time             | `SECOND('10:30:00')` → `0`                                                |

---

### **3. Formatting and Conversion**

|Function|Description|Example|
|---|---|---|
|`DATE_FORMAT(date, format)`|Formats date according to given pattern|`DATE_FORMAT('2024-03-01', '%Y-%m-%d')` → `'2024-03-01'`|
|`STR_TO_DATE(string, format)`|Converts a string to a date|`STR_TO_DATE('01-03-2024', '%d-%m-%Y')` → `'2024-03-01'`|
|`TIME_TO_SEC(time)`|Converts a time value to seconds|`TIME_TO_SEC('01:02:03')` → `3723`|
|`SEC_TO_TIME(seconds)`|Converts seconds to time format|`SEC_TO_TIME(3723)` → `'01:02:03'`|

---

### **4. Current Date and Time**

|Function|Description|Example|
|---|---|---|
|`NOW()`|Returns current date and time|`NOW()` → `'2025-03-18 14:30:00'`|
|`CURDATE()`|Returns current date|`CURDATE()` → `'2025-03-18'`|
|`CURTIME()`|Returns current time|`CURTIME()` → `'14:30:00'`|
|`UTC_DATE()`|Returns current UTC date|`UTC_DATE()` → `'2025-03-18'`|
|`UTC_TIME()`|Returns current UTC time|`UTC_TIME()` → `'12:00:00'`|
|`SYSDATE()`|Returns system's current date and time|`SYSDATE()` → `'2025-03-18 14:30:10'`|

---

### **5. Miscellaneous**

| Function          | Description                                          | Example                                   |
| ----------------- | ---------------------------------------------------- | ----------------------------------------- |
| `LAST_DAY(date)`  | Returns the last day of the month for the given date | `LAST_DAY('2024-03-01')` → `'2024-03-31'` |
| `WEEK(date)`      | Returns the week number (0-53)                       | `WEEK('2024-03-01')` → `9`                |
| `DAYOFWEEK(date)` | Returns the weekday index (1=Sunday, 7=Saturday)     | `DAYOFWEEK('2024-03-01')` → `6 (Friday)`  |
| `DAYOFYEAR(date)` | Returns the day of the year (1-366)                  | `DAYOFYEAR('2024-03-01')` → `61`          |
| `QUARTER(date)`   | Returns the quarter (1-4)                            | `QUARTER('2024-03-01')` → `1`             |
|                   |                                                      |                                           |

---

