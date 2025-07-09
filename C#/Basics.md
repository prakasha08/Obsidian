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