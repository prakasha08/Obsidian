
## 🔹 Java is Strictly **Call by Value**

In Java, **everything is passed by value** — **including objects**. But here's the catch:

- For **primitive types** (like `int`, `double`, `boolean`), the actual **value** is passed.
    
- For **objects** (like arrays, Strings, custom classes), the **reference (or memory address)** is passed **by value**.
    

So you can think of it like:

> Java **passes a copy of the reference** to the object, not the actual object itself and not a reference to the reference.

---

## ✅ Example 1: Primitive Variables

```java
void modify(int x) {
    x = 10;
}

int num = 5;
modify(num);
System.out.println(num); // ➡️ 5
```

### ✅ Explanation:

- A copy of `num` (which is 5) is passed.
    
- `x` becomes 10, but it’s **local to the method**.
    
- `num` remains unchanged.
    

---

## ✅ Example 2: Arrays (Reference Types)

```java
void changeArray(int[] arr) {
    arr[0] = 100;
}

int[] numbers = {1, 2, 3};
changeArray(numbers);
System.out.println(numbers[0]); // ➡️ 100
```

### ✅ Explanation:

- `arr` receives a **copy of the reference** to the array.
    
- Both `arr` and `numbers` refer to the same array in memory.
    
- Modifying elements affects the original array.
    

**But...**

```java
void changeArray(int[] arr) {
    arr = new int[] {9, 9, 9}; // new object
}

int[] numbers = {1, 2, 3};
changeArray(numbers);
System.out.println(numbers[0]); // ➡️ Still 1
```

### ❗ Why?

- The method got a **copy of the reference**.
    
- You changed the copy to point to a new array.
    
- The original reference (`numbers`) outside is untouched.
    

---

## ✅ Example 3: Strings (Immutable Objects)

```java
void modifyString(String s) {
    s = s + " World";
}

String str = "Hello";
modifyString(str);
System.out.println(str); // ➡️ Hello
```

### ✅ Explanation:

- Strings in Java are **immutable**.
    
- The `+` operation creates a **new String object**.
    
- The new reference is assigned to `s`, which is local to the method.
    
- The original `str` remains unchanged.
    

---

## ✅ Example 4: StringBuilder (Mutable Object)

```java
void modifyBuilder(StringBuilder sb) {
    sb.append(" World");
}

StringBuilder sb = new StringBuilder("Hello");
modifyBuilder(sb);
System.out.println(sb); // ➡️ Hello World
```

### ✅ Explanation:

- `StringBuilder` is **mutable**.
    
- The reference copy allows the method to change the contents.
    
- So the changes reflect outside the method.
    

---

## 🧠 Summary Table

|Type|Mutable?|Passed by?|Changes reflect outside?|Notes|
|---|---|---|---|---|
|`int`, `double`|No|Value|❌ No|Primitive|
|`String`|No|Reference (by value)|❌ No|Immutable|
|`StringBuilder`|Yes|Reference (by value)|✅ Yes|Mutable|
|Arrays|Yes|Reference (by value)|✅ Yes (if internal values changed)|See example|

---

## 🔍 Final Tip to Remember

> Java does **not** support Call by Reference.  
> Instead, it **passes a copy of the reference** (i.e., Call by Value of the Reference).

So if you:

- **Change the object’s internal state** → Changes **persist**.(If a method modifies **the contents** of an object, and the object is **mutable**, changes will reflect.)
    
- **Reassign the object reference** → Changes **don’t persist**.(> If a method **reassigns** the object to a new one, that reassignment is **local only**.)

---

Would you like me to create diagrams or memory visuals to help understand these better?