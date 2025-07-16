## Datatypes
![[Pasted image 20250709223256.png]]
![[Pasted image 20250709223300.png]]

## Implicit & Explicit Conversion (Extended)

```csharp
namespace Datatypes
{
    class Program
    {
        static void Main(String[] args)
        {
            float num = 3.1415f;
            int a = (int)num; // Explicit conversion (float to int)
            Console.WriteLine(a); // Output: 3

            int b = 10;
            Console.WriteLine(b.GetType()); // System.Int32

            long num1 = b; // Implicit conversion (int to long)
            Console.WriteLine(num1);
            Console.WriteLine(num1.GetType()); // System.Int64

            // Additional Examples
            double d = 9.78;
            int i = (int)d; // Manual (explicit) casting
            Console.WriteLine(i); // 9

            int small = 100;
            double big = small; // Implicit conversion
            Console.WriteLine(big); // 100.0

            char ch = 'A';
            int ascii = ch; // Implicit
            Console.WriteLine(ascii); // 65

            int num2 = 66;
            char ch2 = (char)num2; // Explicit
            Console.WriteLine(ch2); // 'B'
        }
    }
}
```

---
## Type Conversion (Extended)

```csharp
using System;

namespace Datatypes
{
    class Program
    {
        static void Main(String[] args)
        {
            int a = 10;
            Console.WriteLine(a);              // 10
            Console.WriteLine(a.GetType());    // System.Int32

            string data = a.ToString();
            Console.WriteLine(data);           // "10"
            Console.WriteLine(data.GetType()); // System.String

            // Additional Examples
            double d = 10.5;
            string s = Convert.ToString(d);
            Console.WriteLine(s);              // "10.5"

            bool flag = true;
            string result = flag.ToString();
            Console.WriteLine(result);         // "True"

            // Convert from string
            string input = "123";
            int value = Convert.ToInt32(input);
            Console.WriteLine(value);          // 123

            // Safe conversion using TryParse
            string invalid = "abc";
            bool success = int.TryParse(invalid, out int number);
            Console.WriteLine(success);        // False
            Console.WriteLine(number);         // 0
        }
    }
}
```

---
## Input Reading & Parsing (Extended)

```csharp
using System;

namespace Datatypes
{
    class Program
    {
        static void Main(String[] args)
        {
            Console.WriteLine("Enter Two Numbers");
            string a = Console.ReadLine();
            string b = Console.ReadLine();
            int num1 = Int32.Parse(a);
            int num2 = Int32.Parse(b);
            int c = num1 + num2;
            Console.WriteLine(c); // Sum

            // Additional Methods
            Console.Write("Enter a float: ");
            float f = float.Parse(Console.ReadLine());
            Console.WriteLine("You entered: " + f);

            Console.Write("Enter a double: ");
            double d = Convert.ToDouble(Console.ReadLine());
            Console.WriteLine("Double: " + d);

            // Using TryParse
            Console.Write("Enter a number safely: ");
            string input = Console.ReadLine();
            if (int.TryParse(input, out int safeNum))
            {
                Console.WriteLine("You entered: " + safeNum);
            }
            else
            {
                Console.WriteLine("Invalid input.");
            }
        }
    }
}
```

---

## ✅ String Manipulation / Methods / Operations (Extended)
![[Pasted image 20250709225152.png]]

```csharp
using System;

namespace Datatypes
{
    class Program
    {
        static void Main(String[] args)
        {
            string name = "Karthik";
            int age = 25;
            string location = "Tamil Nadu";
            Console.WriteLine("Hi am " + name + " my age is " + age + " from" + location);
            Console.WriteLine("Hi am {0} my age is {1} from {2}", name, age, location);
            Console.WriteLine($"Hi am {name} my age is {age} from {location}");
            Console.WriteLine($"Hi am {name} \nmy age is {age} from {location}");
            Console.WriteLine(@$"Hi am {name} \n my age is {age} from {location}");

            // String Methods
            string firstName = "KaRthIk";
            string lastName = "P"; 
            Console.WriteLine(firstName.ToUpper() + " " + lastName); // KARTHIK
            Console.WriteLine(firstName.ToLower() + " " + lastName); // karthik
            string fullName = String.Concat("" + firstName, lastName + " ");
            Console.WriteLine(fullName.Trim());
            Console.WriteLine(firstName.Substring(2)); // RthIk

            // Additional String Operations
            Console.WriteLine(firstName.StartsWith("Ka"));  // True
            Console.WriteLine(firstName.EndsWith("Ik"));    // True
            Console.WriteLine(firstName.Contains("th"));    // True
            Console.WriteLine(firstName.Replace("Ka", "Na")); // NaRthIk
            Console.WriteLine(firstName.Insert(0, "Mr. "));  // Mr. KaRthIk
            Console.WriteLine(firstName.Length);             // 7
            Console.WriteLine(firstName[0]);                 // K
            Console.WriteLine(firstName.Equals("karthik", StringComparison.OrdinalIgnoreCase)); // True

            string sentence = "   Hello World!   ";
            Console.WriteLine(sentence.Trim());              // "Hello World!"
            Console.WriteLine(sentence.TrimStart());         // "Hello World!   "
            Console.WriteLine(sentence.TrimEnd());           // "   Hello World!"

            string[] words = "I love CSharp".Split(' ');
            foreach (var word in words)
                Console.WriteLine(word);

            // String Comparison
            string s1 = "apple";
            string s2 = "banana";
            int comp = String.Compare(s1, s2); // -1 if s1 < s2
            Console.WriteLine(comp);
        }
    }
}
```

---
## Console Methods in C#

```csharp
using System;

namespace ConsoleMethods
{
    class Program
    {
        static void Main(string[] args)
        {
            // Console.Write() - Same line
            Console.Write("This is ");
            Console.Write("on the same line.");

            // Console.WriteLine() - New line
            Console.WriteLine(); // Just moves to next line
            Console.WriteLine("This is on a new line.");

            // Console.Read() - Reads a single character as ASCII
            Console.Write("Press any key: ");
            int ascii = Console.Read(); // Waits for input and reads ASCII
            Console.WriteLine("\nASCII Value: " + ascii);
            char character = (char)ascii;
            Console.WriteLine("You typed: " + character);

            // Console.ReadLine() - Raw Input as string
            Console.Write("Enter your name: ");
            string name = Console.ReadLine();
            Console.WriteLine("Hello, " + name);

            // Console.ReadKey() - Hold to Read
            Console.Write("Press any key to continue...");
            Console.ReadKey(); // Waits until a key is pressed
        }
    }
}
```

### 🧠 Summary:

|Method|Description|Input Type|Output Type|
|---|---|---|---|
|`Console.Write()`|Prints on same line|-|-|
|`Console.WriteLine()`|Prints and moves to new line|-|-|
|`Console.Read()`|Reads one character, returns its ASCII|Single char|`int`|
|`Console.ReadLine()`|Reads full line of input as text|Full string|`string`|
|`Console.ReadKey()`|Waits until a key is pressed (does not require Enter)|Single key|`ConsoleKeyInfo`|

---

## ✅ TryParse in C#

### ✨ What is `TryParse()`?

- `TryParse()` **tries to convert** a string to a specific datatype **without throwing an exception**.
    
- If the conversion succeeds, it returns `true` and outputs the converted value.
    
- If it fails (e.g., invalid string), it returns `false` and outputs the default value of the datatype (like 0 for int).
    

### ✅ Syntax

```csharp
bool success = Type.TryParse(string input, out Type result);
```

---

### ✅ Examples

#### 1. Integer Parsing Safely

```csharp
string input = "123";
bool success = int.TryParse(input, out int number);

Console.WriteLine("Success: " + success);  // True
Console.WriteLine("Number: " + number);    // 123
```

#### 2. Invalid Input

```csharp
string input = "abc";
bool success = int.TryParse(input, out int number);

Console.WriteLine("Success: " + success);  // False
Console.WriteLine("Number: " + number);    // 0 (default int)
```

#### 3. With `double`

```csharp
string priceText = "99.99";
bool success = double.TryParse(priceText, out double price);
Console.WriteLine($"Valid: {success}, Price: {price}");
```

#### 4. With `bool`

```csharp
string input = "true";
bool success = bool.TryParse(input, out bool result);
Console.WriteLine(result); // true
```

---

### 🔎 Why Use `TryParse()`?

- **Avoids exceptions**: Unlike `Parse()`, it won't crash on invalid input.
    
- Best for **user input** scenarios where the format is uncertain.
    
- Works with: `int`, `float`, `double`, `bool`, `DateTime`, etc.
    

---



![[Pasted image 20250709231545.png]]

## **Functions in C#**

![[Pasted image 20250710231254.png]]![[Pasted image 20250710231256.png]]


In C#, a **function** (also called a **method**) is a block of code that performs a task. It can **accept inputs**, **perform operations**, and **return results**.

---

### 🔹 Basic Function Syntax:

```csharp
returnType FunctionName(parameterList)
{
    // body
    return value;
}
```

---

### 1. **Function Without Parameters and Return**

```csharp
static void Greet()
{
    Console.WriteLine("Hello from a function!");
}
```

Call it in `Main`:

```csharp
Greet();
```

---

### 2. **Function With Parameters**

```csharp
static void GreetUser(string name)
{
    Console.WriteLine("Hello, " + name + "!");
}
```

```csharp
GreetUser("Prakash");
```

---

### 3. **Function That Returns a Value**

```csharp
static int Add(int a, int b)
{
    return a + b;
}
```

```csharp
int result = Add(10, 5);
Console.WriteLine("Sum: " + result);
```

---

### 4. **Function Overloading (Same Name, Different Parameters)**

```csharp
static int Multiply(int a, int b) => a * b;

static double Multiply(double a, double b) => a * b;
```

---

### 5. **Main Method - Entry Point**

```csharp
static void Main(string[] args)
{
    // this is where your program starts running
}
```

---
### **Var**

- `var` is a **keyword** used to **implicitly declare a variable**, letting the compiler **infer the type** from the value assigned.
    
- Introduced in **C# 3.0**
    
- Still **strongly typed** — once a type is inferred, it **cannot be changed**.
    

---

####  Syntax:

```csharp
var variableName = value;
```

🧠 The type is **determined at compile time** — **not dynamic** like JavaScript.

---

#### Examples:

```csharp
var age = 25;            // Inferred as int
var name = "Prakash";    // Inferred as string
var price = 99.99;       // Inferred as double
var isActive = true;     // Inferred as bool
```

✅ These are **equivalent** to:

```csharp
int age = 25;
string name = "Prakash";
double price = 99.99;
bool isActive = true;
```

---

#### 🚫 Invalid Use of `var`

```csharp
var x; // ❌ Error: Must be initialized
```

- The compiler **must know the type** at the time of declaration.
    

---

#### 💡 Best Practices for `var`

|👍 Use `var` when…|👎 Avoid `var` when…|
|---|---|
|The type is **obvious from the right-hand side**|It makes code **less readable**|
|You're working with **LINQ** or **anonymous types**|You're **learning the language** and need clarity|
|Reducing repetition in **long types**|You assign `null` or unclear types|

---

#### ✅ Real-Life Example:

```csharp
var students = new List<string> { "Ram", "Priya", "Kiran" };

foreach (var student in students)
{
    Console.WriteLine(student);
}
```

---

####  Difference Between `var`, `dynamic`, and `object`

|Feature|`var`|`dynamic`|`object`|
|---|---|---|---|
|Type inferred at compile time|✅ Yes|❌ No (runtime)|❌ No (runtime)|
|Type-safe|✅ Yes|❌ No|❌ No|
|Can change type later|❌ No|✅ Yes|✅ Yes|
|Use case|Clean syntax, known types|COM, JSON, reflection|Boxing/unboxing|

---
### **Operators**

- Arithmetic (`+`, `-`, `*`, `/`, `%`)
    
- Comparison (`==`, `!=`, `<`, `>`, `<=`, `>=`)
    
- Logical (`&&`, `||`, `!`)
    
- Assignment (`=`, `+=`, `-=`, `*=`, `/=`)
    
- Increment/Decrement (`++`, `--`)
    

### **If-Else & Nested Conditions**

- `if`, `else if`, `else`
    
- `switch-case` structure
    

###  **Loops**

- `for` loop
    
- `while` loop
    
- `do-while` loop
    
- `break` and `continue`
    

---

####  Hands-On Practice Code Snippets

---

### Operators Example
![[Pasted image 20250710233017.png]]

```csharp
int a = 10, b = 3;

Console.WriteLine("Sum: " + (a + b));
Console.WriteLine("Modulus: " + (a % b));
Console.WriteLine("a > b? " + (a > b));
Console.WriteLine("Logical AND: " + ((a > 5) && (b < 5)));
```

---

### If-Else Example

```csharp
int num = 15;
if (num > 0)
    Console.WriteLine("Positive");
else if (num < 0)
    Console.WriteLine("Negative");
else
    Console.WriteLine("Zero");
```

---

### Switch Case

```csharp
int day = 3;
switch (day)
{
    case 1: Console.WriteLine("Monday"); break;
    case 2: Console.WriteLine("Tuesday"); break;
    case 3: Console.WriteLine("Wednesday"); break;
    default: Console.WriteLine("Invalid day"); break;
}
```

---

### For Loop

```csharp
for (int i = 1; i <= 5; i++)
{
    Console.WriteLine("Number: " + i);
}
```

---

### While Loop

```csharp
int i = 1;
while (i <= 5)
{
    Console.WriteLine("Count: " + i);
    i++;
}
```

---

### Do While Loop

```csharp
int j = 1;
do
{
    Console.WriteLine("Do While: " + j);
    j++;
} while (j <= 5);
```

### Foreach Loop


🔹 Purpose:

The `foreach` loop is used to iterate over elements in a **collection** or **array** without needing to manage an index manually.

---

#### 🔧 Syntax:

```csharp
foreach (datatype variable in collection)
{
    // code to execute for each element
}
```

---

#### ✅ 1. **Example with an Array**

```csharp
string[] fruits = { "Apple", "Banana", "Mango" };

foreach (string fruit in fruits)
{
    Console.WriteLine(fruit);
}
```

🧾 Output:

```
Apple
Banana
Mango
```

---

#### ✅ 2. **Example with List**

```csharp
List<int> numbers = new List<int> { 10, 20, 30 };

foreach (int num in numbers)
{
    Console.WriteLine("Number: " + num);
}
```

---

#### ✅ 3. **Example with Dictionary**

```csharp
Dictionary<string, int> studentMarks = new Dictionary<string, int>
{
    { "Alice", 90 },
    { "Bob", 85 },
    { "Charlie", 95 }
};

foreach (KeyValuePair<string, int> entry in studentMarks)
{
    Console.WriteLine($"{entry.Key} scored {entry.Value}");
}
```

🧾 Output:

```
Alice scored 90
Bob scored 85
Charlie scored 95
```

---

#### 🧠 Key Notes

|Point|Description|
|---|---|
|✅|Great for **read-only** iterations|
|❌|You **can’t modify** the collection inside a `foreach` directly|
|💡|Use `for` loop if you need index access or to **update elements**|

---

### **Array in C#**

####  Declaration and Initialization

```csharp
int[] numbers = new int[3];                  // Empty array
int[] scores = { 85, 90, 78, 92 };           // Initialized
```

---

#### Looping

```csharp
foreach (int score in scores)
{
    Console.WriteLine(score);
}
```

---

####  **Array Methods (from `System.Array` class)**

|Method / Property|Example|Description|
|---|---|---|
|`Length`|`scores.Length`|Gets total number of elements|
|`Sort()`|`Array.Sort(scores);`|Sorts elements in ascending order|
|`Reverse()`|`Array.Reverse(scores);`|Reverses element order|
|`IndexOf()`|`int i = Array.IndexOf(scores, 90);`|Gets index of a value|
|`LastIndexOf()`|`Array.LastIndexOf(scores, 90);`|Gets last matching index|
|`Copy()`|`Array.Copy(scores, newArray, 4);`|Copies items to another array|
|`Clear()`|`Array.Clear(scores, 1, 2);`|Clears (sets to 0/default) values at given positions|

---

#### Example:

```csharp
int[] scores = { 85, 70, 95, 60 };

// Sort
Array.Sort(scores);  // 60, 70, 85, 95

// Reverse
Array.Reverse(scores);  // 95, 85, 70, 60

// Index
int idx = Array.IndexOf(scores, 85);  // 1

// Copy
int[] copy = new int[4];
Array.Copy(scores, copy, 4);

// Clear
Array.Clear(scores, 1, 2);  // sets index 1 and 2 to 0
```

---

### **ArrayList in C#**

(From `System.Collections`)

#### Declaration

```csharp
ArrayList list = new ArrayList();
list.Add("Apple");
list.Add(100);
list.Add(99.99);
```

---

#### Looping

```csharp
foreach (var item in list)
{
    Console.WriteLine(item);
}
```

---

#### **ArrayList Methods & Properties**

|Method / Property|Example|Description|
|---|---|---|
|`Add()`|`list.Add("New Item");`|Adds element|
|`Insert()`|`list.Insert(1, "Inserted");`|Adds at index|
|`Remove()`|`list.Remove("Apple");`|Removes by value|
|`RemoveAt()`|`list.RemoveAt(2);`|Removes by index|
|`Clear()`|`list.Clear();`|Removes all|
|`Contains()`|`list.Contains(100);`|Checks presence|
|`IndexOf()`|`list.IndexOf(99.99);`|Gets index of item|
|`Count`|`list.Count`|Total number of elements|
|`Sort()`|`list.Sort();`|Sorts elements (same type only!)|
|`Reverse()`|`list.Reverse();`|Reverses order|

---

#### Example:

```csharp
ArrayList items = new ArrayList() { "Book", "Pen", "Pencil" };

// Add
items.Add("Eraser");

// Insert
items.Insert(2, "Sharpener");  // Pen, Sharpener, Pencil...

// Remove
items.Remove("Pen");

// RemoveAt
items.RemoveAt(1);  // Removes at index 1

// Contains
bool hasBook = items.Contains("Book");

// Count
Console.WriteLine("Total: " + items.Count);

// Sort (only if all same type)
ArrayList numbers = new ArrayList() { 10, 2, 5 };
numbers.Sort();  // 2, 5, 10

// Reverse
numbers.Reverse();  // 10, 5, 2
```

---

### **List in C#**

(From `System.Collections.Generic`)

#### Declaration

```csharp
List<int> numbers = new List<int> { 1, 3, 5 };
List<string> names = new List<string>();
```

---

#### Looping

```csharp
foreach (int num in numbers)
{
    Console.WriteLine(num);
}
```

---

#### **List Methods & Properties**

|Method / Property|Example|Description|
|---|---|---|
|`Add()`|`numbers.Add(7);`|Adds item|
|`AddRange()`|`numbers.AddRange(new int[] { 9, 11 });`|Adds multiple items|
|`Insert()`|`numbers.Insert(1, 4);`|Inserts at index|
|`InsertRange()`|`numbers.InsertRange(0, new int[] { 0, 2 });`|Inserts multiple items|
|`Remove()`|`numbers.Remove(3);`|Removes first matching item|
|`RemoveAt()`|`numbers.RemoveAt(2);`|Removes by index|
|`RemoveRange()`|`numbers.RemoveRange(0, 2);`|Removes a group|
|`Contains()`|`numbers.Contains(5);`|Checks if item exists|
|`IndexOf()`|`numbers.IndexOf(11);`|Gets index of item|
|`Sort()`|`numbers.Sort();`|Sorts ascending|
|`Reverse()`|`numbers.Reverse();`|Reverses order|
|`Clear()`|`numbers.Clear();`|Empties list|
|`Count`|`numbers.Count`|Gets size|
|`ToArray()`|`int[] arr = numbers.ToArray();`|Converts to array|

---

#### Example:

```csharp
List<int> numbers = new List<int> { 5, 10, 15 };

// Add
numbers.Add(20);

// AddRange
numbers.AddRange(new int[] { 25, 30 });

// Insert
numbers.Insert(1, 7); // 5, 7, 10, ...

// Remove
numbers.Remove(15);

// Sort + Reverse
numbers.Sort();
numbers.Reverse();

// Convert to array
int[] arr = numbers.ToArray();

// Count
Console.WriteLine("Total: " + numbers.Count);
```

---

#### Final Summary Table

|Feature|`Array`|`ArrayList`|`List<T>`|
|---|---|---|---|
|Type-safe|✅ Yes|❌ No|✅ Yes|
|Resizable|❌ No|✅ Yes|✅ Yes|
|Generic|❌ No|❌ No|✅ Yes|
|Index Access|✅ Yes|✅ Yes|✅ Yes|
|Sort, Reverse|✅ Yes (`Array.Sort`)|✅ Yes|✅ Yes|
|Preferred Use|Fixed size, fast access|Legacy, mixed data|✅ Most used in real-world|

---