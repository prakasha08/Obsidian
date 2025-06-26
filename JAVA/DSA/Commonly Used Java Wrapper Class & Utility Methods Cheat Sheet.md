Here’s a clear list of **common wrapper class methods** and **collection-related methods** in **Java**, including:

- `Integer`, `Double`, `String`, `Character`, etc.
    
- Useful static and instance methods.
    
- With brief usage examples.
    

---

### ✅ 1. **Integer class methods**

|Method|Description|Example|
|---|---|---|
|`Integer.parseInt(String)`|Converts string to int|`int x = Integer.parseInt("123");`|
|`Integer.valueOf(String)`|Converts string to Integer object|`Integer x = Integer.valueOf("123");`|
|`Integer.toString(int)`|Converts int to string|`String s = Integer.toString(123);`|
|`Integer.compare(int a, int b)`|Compares two ints|`Integer.compare(10, 20)` → returns -1|
|`Integer.max(a, b)`|Returns max|`Integer.max(10, 20)` → 20|
|`Integer.min(a, b)`|Returns min|`Integer.min(10, 20)` → 10|
|`Integer.sum(a, b)`|Returns sum|`Integer.sum(5, 7)` → 12|

---

### ✅ 2. **Double class methods**

|Method|Example|
|---|---|
|`Double.parseDouble("12.5")` → `12.5`||
|`Double.valueOf("12.5")` → `Double` object||
|`Double.toString(12.5)` → `"12.5"`||

---

### ✅ 3. **String class methods (commonly used)**

|Method|Description|Example|
|---|---|---|
|`String.valueOf(int)`|Converts primitive to string|`String s = String.valueOf(10);`|
|`s.charAt(index)`|Returns character at position|`s.charAt(0)`|
|`s.length()`|Returns length of string|`s.length()`|
|`s.equals("abc")`|Compares string content||
|`s.contains("a")`|Checks if "a" is in string||
|`s.substring(0, 3)`|Extracts substring||
|`s.split(" ")`|Splits by space||
|`s.trim()`|Removes spaces at ends||

---

### ✅ 4. **Character class methods**

| Method                         | Description                   | Example                               |
| ------------------------------ | ----------------------------- | ------------------------------------- |
| `Character.isDigit(c)`         | Checks if char is digit       | `Character.isDigit('5')`              |
| `Character.isLetter(c)`        | Checks if alphabet            | `Character.isLetter('A')`             |
| `Character.isLowerCase(c)`     | Checks lowercase              |                                       |
| `Character.isUpperCase(c)`     | Checks uppercase              |                                       |
| `Character.toLowerCase(c)`     | Converts to lowercase         |                                       |
| `Character.toUpperCase(c)`     | Converts to uppercase         |                                       |
| `Character.getNumericValue(c)` | Returns numeric value of char | `Character.getNumericValue('A')` → 10 |

---

### ✅ 5. **Collections utility methods (`Collections` class)**

|Method|Description|Example|
|---|---|---|
|`Collections.sort(list)`|Sorts ascending|`Collections.sort(arrList);`|
|`Collections.reverse(list)`|Reverses list||
|`Collections.max(list)`|Gets max value||
|`Collections.min(list)`|Gets min value||
|`Collections.frequency(list, item)`|Counts frequency||
|`Collections.shuffle(list)`|Randomly shuffles elements||

---

### ✅ 6. **Arrays utility methods (`Arrays` class)**

|Method|Description|Example|
|---|---|---|
|`Arrays.sort(array)`|Sort array ascending||
|`Arrays.toString(array)`|Print array as string||
|`Arrays.equals(arr1, arr2)`|Compare arrays||
|`Arrays.copyOf(arr, newLength)`|Copy with new length||
|`Arrays.binarySearch(array, key)`|Search element in sorted array||

---

### ✅ Bonus: Conversions

|Conversion|Code|
|---|---|
|`String` → `int`|`Integer.parseInt("123")`|
|`int` → `String`|`String.valueOf(123)` or `Integer.toString(123)`|
|`char` → `int`|`Character.getNumericValue('9')` or `(int)'9' - '0'`|
|`String` → `char[]`|`"abc".toCharArray()`|
|`char` → `String`|`Character.toString('A')` or `"" + 'A'`|