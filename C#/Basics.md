## Datatypes
![[Pasted image 20250709223256.png]]
![[Pasted image 20250709223300.png]]
#### **What is the default access modifier of a class in C#?**

✅ **Answer: C) internal**  
**Explanation:**  
Classes in C# are `internal` by default, meaning they are accessible within the same assembly only.
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
## **Var**
Declares a variable without knowing the type at compile-time
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
## **Operators**

- Arithmetic (`+`, `-`, `*`, `/`, `%`)
    
- Comparison (`==`, `!=`, `<`, `>`, `<=`, `>=`)
    
- Logical (`&&`, `||`, `!`)
    
- Assignment (`=`, `+=`, `-=`, `*=`, `/=`)
    
- Increment/Decrement (`++`, `--`)
    

## **If-Else & Nested Conditions**

- `if`, `else if`, `else`
    
- `switch-case` structure
    

## **Loops**

- `for` loop
    
- `while` loop
    
- `do-while` loop
    
- `break` and `continue`
    

---

####  Hands-On Practice Code Snippets

---

## Operators Example
![[Pasted image 20250710233017.png]]

```csharp
int a = 10, b = 3;

Console.WriteLine("Sum: " + (a + b));
Console.WriteLine("Modulus: " + (a % b));
Console.WriteLine("a > b? " + (a > b));
Console.WriteLine("Logical AND: " + ((a > 5) && (b < 5)));
```

---

## If-Else Example

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

## Switch Case

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

## For Loop

```csharp
for (int i = 1; i <= 5; i++)
{
    Console.WriteLine("Number: " + i);
}
```

---

## While Loop

```csharp
int i = 1;
while (i <= 5)
{
    Console.WriteLine("Count: " + i);
    i++;
}
```

---

## Do While Loop

```csharp
int j = 1;
do
{
    Console.WriteLine("Do While: " + j);
    j++;
} while (j <= 5);
```

## Foreach Loop


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

## `ref` & `out` & `in` 

In C#, both `ref` and `out` are **parameter modifiers** that allow a method to **modify the value of a variable passed from the calling method**. But there are important differences between them.

---
### 1. `ref` Keyword

####  Purpose:

- Allows a method to **read and modify** the value of a variable passed by reference.
    
- The variable **must be initialized** before being passed to the method.
    

---

####  Syntax:

```csharp
void Modify(ref int x)
{
    x = x + 10;
}

int num = 5;
Modify(ref num); // num becomes 15
```

---

####  Explanation:

- `ref` tells the compiler to **pass the memory reference** of the variable.
    
- Any changes inside the method **directly affect the original variable**.
    

---

#### Real Example:

```csharp
using System;

class Program
{
    static void AddTen(ref int number)
    {
        number += 10;
    }

    static void Main()
    {
        int x = 20;
        AddTen(ref x);
        Console.WriteLine(x); // Output: 30
    }
}
```

---

### 2. `out` Keyword

#### Purpose:

- Used when a method needs to **return multiple values**.
    
- The variable **does not need to be initialized** before being passed.
    
- It **must be assigned** inside the method.
    

---

#### Syntax:

```csharp
void SetValues(out int x)
{
    x = 100;
}

int num;
SetValues(out num); // num is now 100
```

---

#### Real Example:

```csharp
using System;

class Program
{
    static void GetStudentDetails(out string name, out int age)
    {
        name = "Prakash";
        age = 21;
    }

    static void Main()
    {
        string studentName;
        int studentAge;

        GetStudentDetails(out studentName, out studentAge);

        Console.WriteLine($"Name: {studentName}, Age: {studentAge}");
        // Output: Name: Prakash, Age: 21
    }
}
```

---

### 🔁 Comparison Table

***"Behind the scenes, ref and out both have the same implementation; the only difference is how the compiler tracks whether variables are assigned or not.”***

![[Pasted image 20250718155830.png]]

| Feature              | `ref`                           | `out`                            |
| -------------------- | ------------------------------- | -------------------------------- |
| Initialization       | Must be initialized before call | Can be uninitialized before call |
| Assignment in method | Optional                        | Must be assigned                 |
| Direction            | Two-way (in & out)              | One-way (only out)               |
| Use case             | When the input value is needed  | When the method returns a value  |

---

### ✅ When to Use

- Use `ref` when the method **needs to read the existing value** and possibly **modify** it.
    
- Use `out` when the method **only outputs a value**, and you don’t care about the initial value.
    

---

### ✅ Bonus: Multiple Return Values with `out`

```csharp
bool Divide(int a, int b, out int result)
{
    if (b == 0)
    {
        result = 0;
        return false;
    }
    result = a / b;
    return true;
}

int output;
if (Divide(10, 2, out output))
{
    Console.WriteLine("Result: " + output); // 5
}
else
{
    Console.WriteLine("Cannot divide by zero");
}
```

### 3. `in` Keyword 

The `in` keyword in C# is a **parameter modifier** that is used to **pass arguments by reference**, just like `ref` and `out`. However, unlike `ref`, the value **cannot be modified** inside the method. It is **read-only**.

---
#### Purpose:

- Allows a method to **read a parameter by reference**.
    
- Improves **performance** for large structs (avoids copying).
    
- Guarantees that the parameter will **not be modified** inside the method.
    

---

#### Syntax:

```csharp
void PrintValue(in int x)
{
    Console.WriteLine(x); // Can read
    // x = x + 1; ❌ Not allowed
}
```

---

#### Real Example:

```csharp
using System;

class Program
{
    static void Display(in int number)
    {
        Console.WriteLine("The number is: " + number);
        // number++; ❌ Error: Cannot assign to variable passed as in
    }

    static void Main()
    {
        int num = 100;
        Display(in num); // Output: The number is: 100
    }
}
```

---

#### Example with Struct (Performance Use Case):

```csharp
struct LargeStruct
{
    public int A, B, C, D, E;
}

class Program
{
    static void ProcessLargeStruct(in LargeStruct data)
    {
        Console.WriteLine(data.A); // ✅ Read is allowed
        // data.A = 5; ❌ Not allowed
    }

    static void Main()
    {
        LargeStruct s = new LargeStruct { A = 10, B = 20, C = 30, D = 40, E = 50 };
        ProcessLargeStruct(in s);
    }
}
```

---

#### Comparison with `ref` and `out`

|Feature|`ref`|`out`|`in`|
|---|---|---|---|
|Direction|Two-way (in & out)|Out only|In only (readonly)|
|Must initialize before call|✅ Yes|❌ No|✅ Yes|
|Must assign in method|❌ No|✅ Yes|❌ No (cannot assign)|
|Can read value|✅ Yes|❌ No (not guaranteed)|✅ Yes|
|Can modify value|✅ Yes|✅ Yes|❌ No|

---

#### ✅ When to Use

- Use `in` when:
    
    - You want to **optimize performance** by passing large structs **by reference**.
        
    - You want to **protect the value** from being modified inside the method.
        
    - You only need **read-only access**.
        

---

### ✅ Summary

- `in`: Pass by reference, **read-only**.
    
- `ref`: Pass by reference, **read and write**.
    
- `out`: Pass by reference, **write-only (must assign)**.
    

---


# Collections
![[Pasted image 20250716235400.png]]
## **Array 

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

## **ArrayList 

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

## **List

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

| Feature       | `Array`                 | `ArrayList`        | `List<T>`                 |
| ------------- | ----------------------- | ------------------ | ------------------------- |
| Type-safe     | ✅ Yes                   | ❌ No               | ✅ Yes                     |
| Resizable     | ❌ No                    | ✅ Yes              | ✅ Yes                     |
| Generic       | ❌ No                    | ❌ No               | ✅ Yes                     |
| Index Access  | ✅ Yes                   | ✅ Yes              | ✅ Yes                     |
| Sort, Reverse | ✅ Yes (`Array.Sort`)    | ✅ Yes              | ✅ Yes                     |
| Preferred Use | Fixed size, fast access | Legacy, mixed data | ✅ Most used in real-world |

---

## **Hashtable**

- A `Hashtable` **stores key-value pairs**.
    
- It's part of the **`System.Collections`** namespace.
    
- **Keys must be unique**.
    
- **Values can be null or duplicate**.
    
- Keys and values are stored as **objects** (non-generic, unlike `Dictionary<TKey, TValue>`).
    

---

#### 🔧 Syntax

```csharp
using System.Collections;

Hashtable ht = new Hashtable();
```

---

#### Add Elements

```csharp
ht.Add("id", 101);
ht.Add("name", "Alice");
ht.Add("dept", "IT");
```

---

#### Access Values

```csharp
Console.WriteLine(ht["name"]); // Alice
```

---

#### Iterate Over `Hashtable`

```csharp
foreach (DictionaryEntry entry in ht)
{
    Console.WriteLine($"Key: {entry.Key}, Value: {entry.Value}");
}
```

---

#### Check if Key Exists

```csharp
if (ht.ContainsKey("id"))
{
    Console.WriteLine("ID exists.");
}
```

---

#### Check if Value Exists

```csharp
if (ht.ContainsValue("IT"))
{
    Console.WriteLine("Value IT found.");
}
```

---

#### Remove an Element

```csharp
ht.Remove("dept");
```

---

#### Clear All Elements

```csharp
ht.Clear();
```

---

### All Common Methods

|Method|Description|
|---|---|
|`Add(key, value)`|Adds a key-value pair|
|`Remove(key)`|Removes the pair with the given key|
|`ContainsKey(key)`|Returns `true` if the key exists|
|`ContainsValue(val)`|Returns `true` if the value exists|
|`Clear()`|Removes all elements|
|`Count`|Number of elements|
|`Keys`|Collection of all keys|
|`Values`|Collection of all values|

---

#### Example Program

```csharp
using System;
using System.Collections;

class Program
{
    static void Main()
    {
        Hashtable student = new Hashtable();
        student.Add("RollNo", 10);
        student.Add("Name", "Prakash");
        student.Add("Department", "ECE");

        Console.WriteLine("Student Info:");
        foreach (DictionaryEntry entry in student)
        {
            Console.WriteLine($"{entry.Key}: {entry.Value}");
        }

        Console.WriteLine("\nCheck if 'Name' exists: " + student.ContainsKey("Name"));
        Console.WriteLine("Removing Department...");
        student.Remove("Department");

        Console.WriteLine("Updated Info:");
        foreach (DictionaryEntry entry in student)
        {
            Console.WriteLine($"{entry.Key}: {entry.Value}");
        }
    }
}
```

---


## Dictionary

- A `Dictionary<TKey, TValue>` is a generic collection in the `System.Collections.Generic` namespace.
    
- It stores data in key-value pairs.
    
- Keys must be unique.
    
- It is type-safe and provides faster performance than non-generic collections like `Hashtable`.
    

---

#### Syntax

```csharp
Dictionary<string, string> myDict = new Dictionary<string, string>();
```

Or using `var`:

```csharp
var myDict = new Dictionary<string, string>();
```

---

#### Adding Elements

```csharp
myDict.Add("Name", "Prakash");
myDict.Add("Dept", "ECE");
myDict.Add("College", "BIT");
```

---

#### Accessing a Value

```csharp
Console.WriteLine(myDict["Dept"]);  // Output: ECE
```

---

#### Looping Through Dictionary

#### Using `foreach` with `KeyValuePair`:

```csharp
foreach (KeyValuePair<string, string> kvp in myDict)
{
    Console.WriteLine($"Key: {kvp.Key}, Value: {kvp.Value}");
}
```

#### Using `var`:

```csharp
foreach (var kvp in myDict)
{
    Console.WriteLine($"{kvp.Key} => {kvp.Value}");
}
```

#### Using `for

```csharp
for(int i = 0; i < dataBook.Count; i++)
{
Console.WriteLine($" (dataBook. Keys. ElementAt(i)} {dataBook. Values. ElementAt(i))");
}
```
---

#### Checking for Existence

```csharp
myDict.ContainsKey("Name");      // Returns true if key exists
myDict.ContainsValue("ECE");     // Returns true if value exists
```

---

#### Removing Elements

```csharp
myDict.Remove("College");    // Removes entry with key "College"
```

---

#### Clearing the Dictionary

```csharp
myDict.Clear();    // Removes all entries
```

---

#### Common Methods and Properties

|Member|Description|
|---|---|
|`Add(key, value)`|Adds a new key-value pair|
|`Remove(key)`|Removes the entry with the given key|
|`ContainsKey(key)`|Returns true if the key exists|
|`ContainsValue(value)`|Returns true if the value exists|
|`Count`|Gets the number of key-value pairs|
|`Keys`|Gets a collection containing all keys|
|`Values`|Gets a collection containing all values|
|`Clear()`|Removes all key-value pairs|
|`TryGetValue(key, out val)`|Safely gets a value without throwing an exception|

---
#### `TryGetValue`?

##### Purpose:

`TryGetValue` is a **safe way** to get a value from a dictionary **without throwing an exception** if the key is missing.

##### Syntax:

```csharp
if (myDict.TryGetValue("Dept", out string dept))
{
    Console.WriteLine("Value = " + dept);
}
else
{
    Console.WriteLine("Key not found.");
}
```

##### How It Works:

- Checks if the key exists.
    
- If **yes**: assigns the value to `dept` and returns `true`.
    
- If **no**: sets `dept` to default (`null` here) and returns `false`.
    

##### Without TryGetValue:

```csharp
string dept = myDict["Dept"];  // ❌ Throws exception if "Dept" is not present
```

##### Think of `TryGetValue` as:

"**Try** to get the value, and **tell me if it worked**, so I can avoid crashing my program."

---

Let me know if you want to see an example comparing `.TryGetValue` and normal indexing with error handling.

---

##### Full Example

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        Dictionary<string, string> student = new Dictionary<string, string>();
        student.Add("RollNo", "101");
        student.Add("Name", "Prakash");
        student.Add("Dept", "ECE");

        Console.WriteLine("Student Dictionary:");
        foreach (var item in student)
        {
            Console.WriteLine($"{item.Key}: {item.Value}");
        }

        Console.WriteLine("\nRemoving 'Dept'...");
        student.Remove("Dept");

        Console.WriteLine("\nUpdated Dictionary:");
        foreach (var item in student)
        {
            Console.WriteLine($"{item.Key}: {item.Value}");
        }

        Console.WriteLine("\nTotal entries: " + student.Count);
    }
}
```

---

## Dictionary vs Hashtable

| Feature     | Dictionary<TKey, TValue>          | Hashtable                             |
| ----------- | --------------------------------- | ------------------------------------- |
| Type-safety | Yes (Generic, compile-time check) | No (uses object, type-casting needed) |
| Performance | Faster                            | Slower                                |
| Namespace   | `System.Collections.Generic`      | `System.Collections`                  |
| Key Type    | Strongly typed (e.g., `string`)   | Stored as `object`                    |

---

## Stack

A **Stack** is a collection that follows the **LIFO** (Last-In-First-Out) principle. It means the last element added is the first one to be removed.

---

#### Namespace:

```csharp
using System.Collections;          // For non-generic Stack
using System.Collections.Generic; // For generic Stack<T>
```

---

#### Creating a Stack

##### Non-Generic Stack:

```csharp
Stack myStack = new Stack();
myStack.Push(10);
myStack.Push(20);
```

##### Generic Stack:

```csharp
Stack<int> numberStack = new Stack<int>();
numberStack.Push(100);
numberStack.Push(200);
```

---

#### Core Methods in Stack

|Method|Description|
|---|---|
|`Push(item)`|Adds an item to the top of the stack.|
|`Pop()`|Removes and returns the top item.|
|`Peek()`|Returns the top item without removing it.|
|`Clear()`|Removes all items from the stack.|
|`Contains(item)`|Checks whether an item exists in the stack.|
|`Count`|Gets the number of elements in the stack.|
|`ToArray()`|Copies the stack to a new array.|
|`GetEnumerator()`|Returns an enumerator for the stack.|
|`TrimExcess()` (Generic only)|Reduces the capacity to match the count.|
|`CopyTo(array, index)`|Copies elements to an existing array starting from a specific index.|

---

#### Example – Generic Stack

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        Stack<string> names = new Stack<string>();
        names.Push("Alice");
        names.Push("Bob");
        names.Push("Charlie");

        Console.WriteLine("Peek: " + names.Peek()); // Charlie

        Console.WriteLine("Popped: " + names.Pop()); // Charlie

        Console.WriteLine("Contains Bob? " + names.Contains("Bob")); // True

        Console.WriteLine("Count: " + names.Count); // 2

        Console.WriteLine("Items in stack:");
        foreach (var name in names)
        {
            Console.WriteLine(name);
        }
    }
}
```

---

#### Summary

- Use **Stack** when you want to process items in reverse order (last in, first out).
    
- Prefer **`Stack<T>`** (generic) for type safety.
    
- Use `Push`, `Pop`, and `Peek` for core stack operations.
    

---
## Queue in C#

A **Queue** is a collection that follows the **FIFO** (First-In-First-Out) principle. This means the first element added is the first one to be removed.

---

####  Namespace:

```csharp
using System.Collections;          // For non-generic Queue
using System.Collections.Generic; // For generic Queue<T>
```

---

#### Creating a Queue

#### Non-Generic Queue:

```csharp
Queue myQueue = new Queue();
myQueue.Enqueue("A");
myQueue.Enqueue("B");
```

#### Generic Queue:

```csharp
Queue<string> queue = new Queue<string>();
queue.Enqueue("Apple");
queue.Enqueue("Banana");
```

---

#### Core Methods in Queue

|Method|Description|
|---|---|
|`Enqueue(item)`|Adds an item to the end of the queue.|
|`Dequeue()`|Removes and returns the item at the beginning of the queue.|
|`Peek()`|Returns the item at the beginning without removing it.|
|`Clear()`|Removes all items from the queue.|
|`Contains(item)`|Checks if an item exists in the queue.|
|`Count`|Returns the number of elements in the queue.|
|`ToArray()`|Copies the queue to a new array.|
|`TrimExcess()` _(Generic only)_|Sets the capacity to the actual number of elements.|
|`CopyTo(array, index)`|Copies queue elements to an existing array from a specific index.|
|`GetEnumerator()`|Returns an enumerator to iterate through the queue.|

---

#### Example – Generic Queue

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        Queue<string> fruits = new Queue<string>();

        fruits.Enqueue("Apple");
        fruits.Enqueue("Banana");
        fruits.Enqueue("Cherry");

        Console.WriteLine("Peek: " + fruits.Peek());       // Apple
        Console.WriteLine("Dequeue: " + fruits.Dequeue()); // Apple

        Console.WriteLine("Contains Banana? " + fruits.Contains("Banana")); // True
        Console.WriteLine("Count: " + fruits.Count);       // 2

        Console.WriteLine("Items in queue:");
        foreach (string fruit in fruits)
        {
            Console.WriteLine(fruit);
        }
    }
}
```

---

#### Summary

- Use **Queue** when the order of processing needs to be **first come, first served**.
    
- Use **`Queue<T>`** for type-safe collections.
    
- Primary operations: `Enqueue`, `Dequeue`, and `Peek`.
    

---
![[Pasted image 20250720155707.png]]
## 1. Class

### 🔹 What is a Class?

A **class** in C# is a user-defined blueprint or prototype from which objects are created. It can contain fields, methods, constructors, properties, and more.

### 🔹 Syntax:

```csharp
class ClassName
{
    // Fields
    // Constructors
    // Methods
    // Properties (Getters/Setters)
}
```

### 🔹 Example:

```csharp
class Person
{
    public string name;
    public int age;

    public void Greet()
    {
        Console.WriteLine($"Hello, I am {name} and I am {age} years old.");
    }
}
```

---

## 2. Object

### 🔹 What is an Object?

An **object** is an instance of a class. When a class is defined, no memory is allocated. Memory is allocated only when an object is created.

### 🔹 Syntax:

```csharp
ClassName obj = new ClassName();
```

### 🔹 Example:

```csharp
Person p1 = new Person();
p1.name = "John";
p1.age = 25;
p1.Greet(); // Output: Hello, I am John and I am 25 years old.
```

---

## 3. Constructor

###  What is a Constructor?

A **constructor** is a special method that gets called automatically when an object is created. It is used to initialize the object.

- Constructor name = class name
    
- No return type (not even `void`)
    
- Can be **default**, **parameterized**, or **overloaded**
    

---

###  Types of Constructors

####  a) Default Constructor

Automatically provided if no constructor is written.

```csharp
class Animal
{
    public string type = "Dog";
    
    // Default constructor
    public Animal()
    {
        Console.WriteLine("Animal created!");
    }

    public void ShowType()
    {
        Console.WriteLine($"Type: {type}");
    }
}

// Usage
Animal a = new Animal(); // Output: Animal created!
a.ShowType();             // Output: Type: Dog
```

---

#### b) Parameterized Constructor

Used to pass values when creating the object.

```csharp
class Book
{
    public string title;
    public int price;

    public Book(string t, int p)
    {
        title = t;
        price = p;
    }

    public void Info()
    {
        Console.WriteLine($"Book: {title}, Price: ₹{price}");
    }
}

// Usage
Book b = new Book("C# Basics", 350);
b.Info(); // Output: Book: C# Basics, Price: ₹350
```

---

### Constructor Overloading (Multiple Constructors)

Constructor overloading means defining **more than one constructor** with different parameters.

```csharp
class Student
{
    public string name;
    public int age;

    // Default constructor
    public Student()
    {
        name = "Unknown";
        age = 0;
    }

    // Parameterized constructor
    public Student(string n, int a)
    {
        name = n;
        age = a;
    }

    public void Print()
    {
        Console.WriteLine($"Name: {name}, Age: {age}");
    }
}

// Usage
Student s1 = new Student();
Student s2 = new Student("Alice", 21);

s1.Print(); // Output: Name: Unknown, Age: 0
s2.Print(); // Output: Name: Alice, Age: 21
```

---

### Getter and Setter (Encapsulation)

#### 🔹 What is Encapsulation?

Encapsulation = Wrapping fields with `get` and `set` methods to **control access**.

- Improves security and flexibility.
    
- Prevents direct access to fields from outside.
    

---

#### 🔹 Syntax:

```csharp
private int _marks;

public int Marks
{
    get { return _marks; }
    set { _marks = value; }
}
```

Or using **auto-implemented properties**:

```csharp
public int Age { get; set; }
```

---

#### 🔹 Example with Getters and Setters:

```csharp
class Employee
{
    private string name;
    private int salary;

    public string Name
    {
        get { return name; }
        set { name = value; }
    }
    //or
    public string Name { get; set; }

    public int Salary
    {
        get { return salary; }
        set
        {
            if (value > 0)
                salary = value;
            else
                salary = 0;
        }
    }

    public void Show()
    {
        Console.WriteLine($"Employee: {name}, Salary: ₹{salary}");
    }
}

// Usage
Employee emp = new Employee();
emp.Name = "Kiran";
emp.Salary = 50000;
emp.Show(); // Output: Employee: Kiran, Salary: ₹50000
```

---
### `this` Keyword 

The `this` keyword refers to the **current instance of the class**. It is used to:

- Access current class members (fields, constructors, methods)
    
- Differentiate between local variables and instance variables when they have the same name
    
- Pass the current object as a parameter
    

---

#### 🟩 Example 1: Using `this` to Differentiate Variables

```csharp
class Student
{
    string name;

    public Student(string name)
    {
        this.name = name;  // Refers to the instance variable
    }

    public void Display()
    {
        Console.WriteLine("Student Name: " + this.name);
    }
}

class Program
{
    static void Main()
    {
        Student s1 = new Student("Prakash");
        s1.Display();  // Output: Student Name: Prakash
    }
}
```

---

#### 🟩 Example 2: `this` in Method Chaining

```csharp
class Calculator
{
    int result = 0;

    public Calculator Add(int x)
    {
        result += x;
        return this;
    }

    public Calculator Multiply(int y)
    {
        result *= y;
        return this;
    }

    public void Print()
    {
        Console.WriteLine("Result: " + result);
    }
}

class Program
{
    static void Main()
    {
        Calculator calc = new Calculator();
        calc.Add(5).Multiply(2).Print();  // Output: Result: 10
    }
}
```

```c#
	class Person
{
    private string name;
    private int age;

    public Person SetName(string name)
    {
        this.name = name;
        return this; // Return the current object
    }

    public Person SetAge(int age)
    {
        this.age = age;
        return this; // Return the current object
    }

    public Person Display()
    {
        Console.WriteLine($"Name: {name}, Age: {age}");
        return this; // Optional: allows further chaining
    }
}
class Program
{
    static void Main()
    {
        Person p = new Person();
        p.SetName("Prakash").SetAge(22).Display();
    }
}
```
---

### Static vs Instance Members in C#

In C#, **static members** belong to the **class itself**, while **instance members** belong to an **object** of the class.

|Feature|Static Members|Instance Members|
|---|---|---|
|Memory Allocation|Only once, shared across all objects|Each object has its own copy|
|Accessed by|Class name|Object name|
|Use case|Common/shared data|Object-specific data|
|Keyword|`static`|(No keyword needed)|

---

#### 🟩 Example: Static vs Instance

```csharp
class Employee
{
    public string name;              // Instance member
    public static string company;    // Static member

    public void Display()
    {
        Console.WriteLine("Name: " + name + ", Company: " + company);
    }
}

class Program
{
    static void Main()
    {
        Employee.company = "Google";  // Set static field

        Employee emp1 = new Employee();
        emp1.name = "Alice";
        emp1.Display();  // Output: Name: Alice, Company: Google

        Employee emp2 = new Employee();
        emp2.name = "Bob";
        emp2.Display();  // Output: Name: Bob, Company: Google
    }
}
```

> Even though `company` was not set separately for `emp1` and `emp2`, both access the same shared static field.

---

#### 🟨 Static Methods

- Can only access static members
    
- Cannot use `this` keyword
    
- Called using the class name
    

```csharp
class Utility
{
    public static void PrintGreeting()
    {
        Console.WriteLine("Welcome to C# World!");
    }
}

class Program
{
    static void Main()
    {
        Utility.PrintGreeting();  // Calling static method
    }
}
```

---
![[Pasted image 20250720215124.png]]
## Inheritance

**Inheritance** is an object-oriented concept where a **child (derived) class** inherits members (fields, properties, methods) from a **parent (base) class**.  
This promotes **code reusability** and **hierarchical classification**.

---

#### Why use Inheritance?

- Reuse common functionality
    
- Avoid code duplication
    
- Establish relationships between classes
    
- Enable **polymorphism**
    

---

#### Syntax

```csharp
class BaseClass
{
    // fields, properties, methods
}

class DerivedClass : BaseClass
{
    // additional members or overridden behavior
}
```

---

### Single Inheritance

In **Single Inheritance**, one class inherits from **one base class**.
#### Example

```csharp
class Animal
{
    public void Eat()
    {
        Console.WriteLine("Animal is eating");
    }
}

class Dog : Animal // Dog inherits from Animal
{
    public void Bark()
    {
        Console.WriteLine("Dog is barking");
    }
}
```

---

#### Usage

```csharp
class Program
{
    static void Main()
    {
        Dog d = new Dog();
        d.Eat();  // Inherited from Animal
        d.Bark(); // Defined in Dog
    }
}
```

**Output:**

```
Animal is eating  
Dog is barking
```

---

#### Key Points

|Term|Description|
|---|---|
|Base Class|The class whose members are inherited (e.g., `Animal`)|
|Derived Class|The class that inherits (e.g., `Dog`)|
|`:` Symbol|Used to specify inheritance in C#|
|Inherited Members|`public` and `protected` members are inherited|
|Access Modifiers|`private` members are **not** inherited directly|

---

#### Real-world Analogy

Think of a **base class** like a general blueprint (e.g., _Vehicle_), and the **derived class** as a specific version (e.g., _Car_). A _Car_ is a _Vehicle_ but has some additional features.

---
#### Example Approach 1: 

```csharp
using System;

public class Company
{
    // Properties
    public int CompanyId { get; set; }
    public string CompanyName { get; set; }
    public string Location { get; set; }

    // Constructor
    public Company(int companyId, string companyName, string location)
    {
        CompanyId = companyId;
        CompanyName = companyName;
        Location = location;
    }

    // Method
    public void DisplayCompanyDetails()
    {
        Console.WriteLine($"Id: {CompanyId} | Name: {CompanyName} | Location: {Location}");
    }

    public void DisplayData()
    {
        Console.WriteLine($"Id: {CompanyId} | Name: {CompanyName}");
    }
}

// Derived class - inherits from Company
public class Employee : Company
{
    // Additional properties for Employee
    public int EmployeeId { get; set; }
    public string EmployeeName { get; set; }
    public string Address { get; set; }

    // Constructor
    public Employee(int companyId, string companyName, string location)
        : base(companyId, companyName, location)  // calling base class constructor
    {
        // Can initialize Employee-specific values here if passed as parameters
    }
    /*or
    public Employee(int employeeid, string employeeName, string address, int companyId, string companyName, string location): base (companyId, companyName, location){
    }*/
}

class Program
{
    static void Main(string[] args)
    {
        // Creating Employee object, which also has company info due to inheritance
        Employee googleEmployee = new Employee(1, "Google", "India");

        // Accessing base class method
        googleEmployee.DisplayCompanyDetails();

        // You can also assign employee-specific data now:
        googleEmployee.EmployeeId = 101;
        googleEmployee.EmployeeName = "Prakash";
        googleEmployee.Address = "Chennai";

        Console.WriteLine($"Employee Id: {googleEmployee.EmployeeId}");
        Console.WriteLine($"Employee Name: {googleEmployee.EmployeeName}");
        Console.WriteLine($"Address: {googleEmployee.Address}");
    }
}
```

---

##### 🧠 Concept Breakdown

##### Base Class: `Company`

- **Has company-level details** like `CompanyId`, `CompanyName`, and `Location`.
    
- Has methods like `DisplayCompanyDetails()` and `DisplayData()` to show company info.
    

---

##### Derived Class: `Employee : Company`

- **Inherits all members from `Company`**.
    
- Adds employee-specific members:
    
    - `EmployeeId`
        
    - `EmployeeName`
        
    - `Address`
        
- Calls the **base constructor** using `: base(...)` to initialize inherited members.
    

---

##### Output:

```
Id: 1 | Name: Google | Location: India
Employee Id: 101
Employee Name: Prakash
Address: Chennai
```

---

##### Why This Works?

|What Happened|Explanation|
|---|---|
|`Employee` object created|Inherits `Company` members via `: base(...)` constructor|
|Called `DisplayCompanyDetails()`|Defined in `Company` but works through `Employee` object|
|Set employee info|Done separately on top of inherited company info|

---

##### Real-World Analogy

Imagine:

- **Company** is a base structure (like Google).
    
- **Employee** is part of the company but has extra info (like name, ID, address).
    
- Even though the employee object is used, it carries **company identity** too.
    

---
#### Example Approach 2:

##### `Company` class

```csharp
public class Company
{
    public int CompanyId { get; set; }
    public string CompanyName { get; set; }
    public string Location { get; set; }

    public Company(int companyId, string companyName, string location)
    {
        CompanyId = companyId;
        CompanyName = companyName;
        Location = location;
    }

    public void DisplayCompanyDetails()
    {
        Console.WriteLine($"Company ID: {CompanyId}, Name: {CompanyName}, Location: {Location}");
    }
}
```

---

##### `Employee` class

```csharp
public class Employee
{
    public int EmployeeId { get; set; }
    public string EmployeeName { get; set; }
    public string Address { get; set; }

    // ✅ Company property inside Employee
    public Company Company { get; set; }

    // ✅ Constructor that takes both employee details and a Company object
    public Employee(int employeeId, string employeeName, string address, Company company)
    {
        EmployeeId = employeeId;
        EmployeeName = employeeName;
        Address = address;
        Company = company; // Assign the passed-in Company object
    }

    public void DisplayEmployeeDetails()
    {
        Console.WriteLine($"Employee ID: {EmployeeId}, Name: {EmployeeName}, Address: {Address}");
        Console.WriteLine("Belongs to Company:");
        Company.DisplayCompanyDetails(); // Using the company's method
    }
}
```

---

##### `Main` Method (Usage Example)

```csharp
class Program
{
    static void Main(string[] args)
    {
        // Create a company object
        Company google = new Company(1, "Google", "India");

        // Create an employee and assign the company to it
        Employee emp = new Employee(1001, "Prakash", "Chennai", google);

        // Display employee and their company details
        emp.DisplayEmployeeDetails();
    }
}
```

---

##### Output

```
Employee ID: 1001, Name: Prakash, Address: Chennai
Belongs to Company:
Company ID: 1, Name: Google, Location: India
```

---

##### Key Points

| Concept              | Explanation                                            |
| -------------------- | ------------------------------------------------------ |
| "has-a" relationship | `Employee` has a property of type `Company`            |
| Code reuse           | You don't need inheritance if it's just a reference    |
| Flexibility          | One company object can be shared by multiple employees |

---
#### Example Approach 3:
#### Goal:

- Pass **company details and employee details** all in one go to the `Employee` constructor.
    
- Inside the `Employee` constructor, it should create and assign a new `Company` object.
    

---

#### `Company` class (no changes)

```csharp
public class Company
{
    public int CompanyId { get; set; }
    public string CompanyName { get; set; }
    public string Location { get; set; }

    public Company(int companyId, string companyName, string location)
    {
        CompanyId = companyId;
        CompanyName = companyName;
        Location = location;
    }

    public void DisplayCompanyDetails()
    {
        Console.WriteLine($"Company ID: {CompanyId}, Name: {CompanyName}, Location: {Location}");
    }
}
```

---

#### `Employee` class (constructor creates Company object internally)

```csharp
public class Employee
{
    public int EmployeeId { get; set; }
    public string EmployeeName { get; set; }
    public string Address { get; set; }

    public Company Company { get; set; }  // "Has-a" relationship

    // ✅ Constructor takes both employee & company details
    public Employee(int employeeId, string employeeName, string address,
                    int companyId, string companyName, string location)
    {
        EmployeeId = employeeId;
        EmployeeName = employeeName;
        Address = address;

        // Initialize Company using the parameters
        Company = new Company(companyId, companyName, location);
    }

    public void DisplayEmployeeDetails()
    {
        Console.WriteLine($"Employee ID: {EmployeeId}, Name: {EmployeeName}, Address: {Address}");
        Console.WriteLine("Company Details:");
        Company.DisplayCompanyDetails();
    }
}
```

---

#### `Main` Method (Usage Example)

```csharp
class Program
{
    static void Main(string[] args)
    {
        // Just one constructor call handles both employee and company
        Employee emp = new Employee(1001, "Prakash", "Chennai", 101, "Google", "India");

        emp.DisplayEmployeeDetails();
    }
}
```

---

#### Output

```
Employee ID: 1001, Name: Prakash, Address: Chennai
Company Details:
Company ID: 101, Name: Google, Location: India
```

---

#### Summary

|Feature|Purpose|
|---|---|
|`Company` created inside `Employee`|Saves extra steps in main method|
|Good for tight coupling|When employee always belongs to one company|
|Flexible|If you want to still use the previous approach, just overload the constructor|

---
## Multilevel Inheritance

###  What is Multilevel Inheritance?

Multilevel inheritance is when a class is derived from a class which is also derived from another class.

```
Company  →  Employee  →  Developer
```

- `Employee` inherits from `Company`
    
- `Developer` inherits from `Employee`
    

---

### Why Use Multilevel Inheritance?

It helps in reusing code across hierarchical levels and logically grouping functionalities.  
Each derived class adds its own specific behavior.

---

### Example: Company → Employee → Developer

####  `Company` Class (Base class)

```csharp
public class Company
{
    public int CompanyId { get; set; }
    public string CompanyName { get; set; }

    public Company(int companyId, string companyName)
    {
        CompanyId = companyId;
        CompanyName = companyName;
    }

    public void DisplayCompany()
    {
        Console.WriteLine($"Company ID: {CompanyId}, Name: {CompanyName}");
    }
}
```

---

#### `Employee` Class (Derived from Company)

```csharp
public class Employee : Company
{
    public int EmployeeId { get; set; }
    public string EmployeeName { get; set; }

    public Employee(int companyId, string companyName,
                    int employeeId, string employeeName)
        : base(companyId, companyName) // Call base constructor
    {
        EmployeeId = employeeId;
        EmployeeName = employeeName;
    }

    public void DisplayEmployee()
    {
        Console.WriteLine($"Employee ID: {EmployeeId}, Name: {EmployeeName}");
        DisplayCompany(); // Show company too
    }
}
```

---

#### `Developer` Class (Derived from Employee)

```csharp
public class Developer : Employee
{
    public string ProgrammingLanguage { get; set; }

    public Developer(int companyId, string companyName,
                     int employeeId, string employeeName,
                     string programmingLanguage)
        : base(companyId, companyName, employeeId, employeeName)
    {
        ProgrammingLanguage = programmingLanguage;
    }

    public void DisplayDeveloper()
    {
        Console.WriteLine($"Programming Language: {ProgrammingLanguage}");
        DisplayEmployee(); // Show employee + company
    }
}
```

---

#### `Main()` Method

```csharp
class Program
{
    static void Main(string[] args)
    {
        Developer dev = new Developer(101, "Microsoft", 2001, "Prakash", "C#");
        dev.DisplayDeveloper();
    }
}
```

---

#### Output:

```
Programming Language: C#
Employee ID: 2001, Name: Prakash
Company ID: 101, Name: Microsoft
```

---

### Summary Table

|Class|Inherits From|Properties Introduced|
|---|---|---|
|`Company`|-|CompanyId, CompanyName|
|`Employee`|`Company`|EmployeeId, EmployeeName|
|`Developer`|`Employee`|ProgrammingLanguage|

---

### Key Concepts Used:

- `: base(...)` → Calls parent class constructor
    
- Method chaining across inheritance levels
    
- Clean and reusable hierarchy
    

---
## Hierarchical Inheritance 

### ✅ What is Hierarchical Inheritance?

**Hierarchical Inheritance** means **multiple classes inherit from a single base class**.

```
            Company
            /     \
      Employee   Customer
```

- `Employee` and `Customer` both inherit from `Company`.
    
- They can reuse company-related properties/methods but also have their own.
    

---

### Example: Company → Employee and Customer

####  `Company` Class (Base Class)

```csharp
public class Company
{
    public int CompanyId { get; set; }
    public string CompanyName { get; set; }

    public Company(int companyId, string companyName)
    {
        CompanyId = companyId;
        CompanyName = companyName;
    }

    public void DisplayCompany()
    {
        Console.WriteLine($"Company ID: {CompanyId}, Name: {CompanyName}");
    }
}
```

---

#### `Employee` Class (Inherits from Company)

```csharp
public class Employee : Company
{
    public int EmployeeId { get; set; }
    public string EmployeeName { get; set; }

    public Employee(int companyId, string companyName,
                    int employeeId, string employeeName)
        : base(companyId, companyName)
    {
        EmployeeId = employeeId;
        EmployeeName = employeeName;
    }

    public void DisplayEmployee()
    {
        Console.WriteLine($"Employee ID: {EmployeeId}, Name: {EmployeeName}");
        DisplayCompany();
    }
}
```

---

#### `Customer` Class (Inherits from Company)

```csharp
public class Customer : Company
{
    public int CustomerId { get; set; }
    public string CustomerName { get; set; }

    public Customer(int companyId, string companyName,
                    int customerId, string customerName)
        : base(companyId, companyName)
    {
        CustomerId = customerId;
        CustomerName = customerName;
    }

    public void DisplayCustomer()
    {
        Console.WriteLine($"Customer ID: {CustomerId}, Name: {CustomerName}");
        DisplayCompany();
    }
}
```

---

#### `Main()` Method

```csharp
class Program
{
    static void Main(string[] args)
    {
        Employee emp = new Employee(101, "TCS", 2001, "Prakash");
        emp.DisplayEmployee();

        Console.WriteLine();

        Customer cust = new Customer(101, "TCS", 3001, "Suresh");
        cust.DisplayCustomer();
    }
}
```

---

#### Output

```
Employee ID: 2001, Name: Prakash
Company ID: 101, Name: TCS

Customer ID: 3001, Name: Suresh
Company ID: 101, Name: TCS
```

---

### Key Points

|Feature|Company|Employee|Customer|
|---|---|---|---|
|Inherits From|—|`Company`|`Company`|
|Properties|CompanyId, CompanyName|+ EmployeeId, EmployeeName|+ CustomerId, CustomerName|
|Shared Method|`DisplayCompany()`|✔ Reused|✔ Reused|

---

### Why Hierarchical Inheritance?

- Promotes **code reuse** for common data.
    
- Organizes logically similar entities (e.g., all have company info).
    
- Reduces duplication.
    

---

## Multiple Inheritance (via Interfaces)

n C#, **multiple inheritance** (i.e., one class directly inheriting from more than one base class) is **not supported** with **classes** due to the **diamond problem** and ambiguity it can create. But C# solves this using **interfaces**.
### What is it?

> **Multiple inheritance** is when a class **inherits behaviors from more than one parent**, and in C#, this is done using **interfaces**.

---

### Example: `Employee` inherits from `Company` (class) and `IPerson`, `ISalary` (interfaces)

Let’s build on your example with:

- `Company` as a base class (regular class)
    
- `IPerson` interface: provides personal info
    
- `ISalary` interface: provides salary info
    
- `Employee` class inherits from `Company`, `IPerson`, and `ISalary`
    

---

#### `Company` (Base class)

```csharp
public class Company
{
    public string CompanyName { get; set; }

    public Company(string companyName)
    {
        CompanyName = companyName;
    }

    public void DisplayCompany()
    {
        Console.WriteLine("Company: " + CompanyName);
    }
}
```

---

#### `IPerson` Interface

```csharp
public interface IPerson
{
    void DisplayPersonalInfo();
}
```

---

#### `ISalary` Interface

```csharp
public interface ISalary
{
    void DisplaySalary();
}
```

---

#### `Employee` (inherits from 1 class + 2 interfaces)

```csharp
public class Employee : Company, IPerson, ISalary
{
    public string Name { get; set; }
    public int Salary { get; set; }

    public Employee(string companyName, string name, int salary)
        : base(companyName)
    {
        Name = name;
        Salary = salary;
    }

    public void DisplayPersonalInfo()
    {
        Console.WriteLine("Employee Name: " + Name);
    }

    public void DisplaySalary()
    {
        Console.WriteLine("Salary: $" + Salary);
    }
}
```

---

#### `Main()` Method

```csharp
class Program
{
    static void Main(string[] args)
    {
        Employee emp = new Employee("Infosys", "Prakash", 60000);

        emp.DisplayCompany();
        emp.DisplayPersonalInfo();
        emp.DisplaySalary();
    }
}
```

---

#### Output:

```
Company: Infosys
Employee Name: Prakash
Salary: $60000
```

---

### Summary

|Feature|Description|
|---|---|
|Multiple Inheritance|✅ Achieved using interfaces|
|Class Inheritance|❌ C# does not support inheriting multiple classes|
|Interfaces Used|`IPerson`, `ISalary`|
|One Concrete Base Class|`Company`|

## Polymorphism

Polymorphism means **“many forms”**. It allows objects to behave differently based on their data or class. In **C#**, polymorphism lets you define multiple behaviors for the same method name in different contexts.

There are **2 types of polymorphism** in C#:

1. **Compile-Time (Static) Polymorphism** → Achieved by **Method Overloading**
    
2. **Run-Time (Dynamic) Polymorphism** → Achieved by **Method Overriding**
    

---

### 1. **Method Overloading** (Compile-Time Polymorphism)

#### Definition:

In **method overloading**, **multiple methods** in the same class **have the same name** but **different parameters** (different type or count or order).

#### Why use it?

- To perform similar operations with different input types or numbers.
    

#### Syntax:

```csharp
public class Calculator
{
    public int Add(int a, int b)
    {
        return a + b;
    }

    public double Add(double a, double b)
    {
        return a + b;
    }

    public int Add(int a, int b, int c)
    {
        return a + b + c;
    }
}
```

#### Usage:

```csharp
Calculator calc = new Calculator();
Console.WriteLine(calc.Add(2, 3));         // Output: 5
Console.WriteLine(calc.Add(2.5, 3.7));     // Output: 6.2
Console.WriteLine(calc.Add(1, 2, 3));      // Output: 6
```

#### Rules:

- Same method name
    
- Different parameter type/number/order
    
- Must be in the **same class**
    

---

### 2. **Method Overriding** (Run-Time Polymorphism)

#### Definition:

In **method overriding**, a **derived class provides a specific implementation** of a method that is already defined in its base class.

#### Why use it?

- To **change or extend** the functionality of a method inherited from the base class.
    

#### Syntax:

Use `virtual` in base class and `override` in derived class.

```csharp
public class Animal
{
    public virtual void MakeSound()
    {
        Console.WriteLine("Animal makes sound");
    }
}

public class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Dog barks");
    }
}
```

#### Usage:

```csharp
Animal a = new Animal();
a.MakeSound(); // Output: Animal makes sound

Animal b = new Dog();
b.MakeSound(); // Output: Dog barks
```

#### Important Keywords:

- `virtual`: Marks a method that **can be overridden**
    
- `override`: Used in the child class to **override** the virtual method
    
- `base`: Refers to the base class version of the method
    

---

### Comparison: Overloading vs Overriding

|Feature|Overloading|Overriding|
|---|---|---|
|Type|Compile-time (Static)|Run-time (Dynamic)|
|Signature|Must be different|Must be same|
|Class|Same class|Different (Inheritance needed)|
|Keywords|None|`virtual`, `override`|

---

### Example Combining Both:

```csharp
public class Printer
{
    public virtual void Print()
    {
        Console.WriteLine("Printing...");
    }

    // Overloaded
    public void Print(string msg)
    {
        Console.WriteLine("Printing message: " + msg);
    }
}

public class ColorPrinter : Printer
{
    // Overriding
    public override void Print()
    {
        Console.WriteLine("Printing in color...");
    }
}
```

### Usage:

```csharp
Printer p = new Printer();
p.Print();                 // Printing...
p.Print("Hello");          // Printing message: Hello

Printer cp = new ColorPrinter();
cp.Print();                // Printing in color...
```

---

### Summary:

- Use **method overloading** when methods do **similar tasks with different inputs**.
    
- Use **method overriding** when a subclass needs to **customize** behavior from a superclass.
    
- Both enable **polymorphic behavior** that makes your code flexible and reusable.
    

---

## Method Hiding

### 🔹 What is Method Hiding in C#?

**Method Hiding** occurs when a derived class defines a method with the **same name** as a method in the base class **without using `override`**, and instead uses the `new` keyword.

This hides the base class implementation when the object is accessed through the derived class type.

---

### 🔸 Syntax of Method Hiding

```csharp
class BaseClass {
    public void Display() {
        Console.WriteLine("Display from BaseClass");
    }
}

class DerivedClass : BaseClass {
    public new void Display() {
        Console.WriteLine("Display from DerivedClass");
    }
}
```

---

### 🔸 Example: Method Hiding vs Method Overriding

```csharp
using System;

class Animal {
    public void Speak() {
        Console.WriteLine("Animal speaks");
    }
}

class Dog : Animal {
    public new void Speak() {
        Console.WriteLine("Dog barks");
    }
}

class Program {
    static void Main() {
        Animal a = new Dog();    // Base class reference
        Dog d = new Dog();       // Derived class reference
//if new is not there in speak method in dog then parent method will be called
        a.Speak();   // Output: Animal speaks  → because method is hidden, not overridden
        d.Speak();   // Output: Dog barks
    }
}
```

---

### 🔹 Key Points to Remember

|Feature|Method Hiding|Method Overriding|
|---|---|---|
|Keyword used|`new`|`override`|
|Type of method|Normal (non-virtual)|`virtual` in base, `override` in derived|
|Determined by|Reference type|Object type|
|Inheritance behavior|Hides base class method|Replaces base class method|

---

### 🔸 When to Use Method Hiding?

- When you want to **redefine** the behavior of a method **only when using the derived class type**.
    
- Not typically recommended unless absolutely needed — **method overriding** is the better approach in most cases.
    

---

### 🔸 Real-Life Analogy

Imagine a **BaseClass** is a general **Printer**:

- It has a method `Print()` that prints in black and white.
    

Now in the derived class **ColorPrinter**, you define a new `Print()` method:

- If you **override**, every printer reference behaves as a color printer if the object is a ColorPrinter.
    
- If you **hide** it, the behavior depends on the **reference type** (whether you use a `Printer` or `ColorPrinter` reference).
    

---

### 🔹 Best Practices

- Prefer **overriding** with `virtual`/`override` when polymorphism is intended.
    
- Use **method hiding** only when you explicitly want to define completely separate method behavior for derived classes — and don’t want polymorphism.
    

---
