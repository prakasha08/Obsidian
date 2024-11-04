# Generics

by the following we can only customize an Integer Array Only (Other types are not poosible to customize,possible only if we can write same code for each nd every types. So we go for a generics 

![[Pasted image 20240919182737.png]]]]![[Pasted image 20240919182635.png]]![[Pasted image 20240919182637.png]]Generics provide a Parameterized type .
![[Pasted image 20240919183203.png]]
***Above means ArrayList Have only 'Integer'(Generics) (Parameterized type) objects.
If you does not provide any type it will allow any type of value(Type safety).
Detailed Explanation in Below
![[Pasted image 20240919183626.png]]
Generics in Java are a powerful feature that allows for the creation of classes, interfaces, and methods that can operate on any data type, while ensuring type safety at compile time. Without generics, code would need to be written and repeated for every different data type, which can lead to redundancy and potential errors. Below is an explanation based on the images and the context you provided.

---

### Customizing Integer Arrays

In the first part, you're stating that without generics, we can only customize an integer array, which means we'd have to write code specifically tailored for handling integers. If we wanted to work with other data types (e.g., `Double`, `String`), we would need to rewrite the same code for each type. This leads to repetitive code and increases the likelihood of errors. 

This is where **Generics** come in to provide a solution, allowing you to write more reusable and flexible code.

---

### Generics Overview

Generics provide a way to parameterize types, meaning you can write a class, interface, or method that works with any type, while maintaining strong type safety. The primary advantage of generics is that it allows the same code to be reused for different data types without sacrificing the type checking that Java offers at compile time.

For example, consider an `ArrayList<Integer>`. This is a parameterized type, which means that the `ArrayList` is restricted to holding only `Integer` objects. This is done by using the syntax `ArrayList<Integer>`, where `Integer` is the parameterized type.

---

### Parameterized Types in Generics

The concept of a parameterized type means that you can define a class or method with a placeholder for the data type. When you instantiate an object of that class or call the method, you specify the actual data type (such as `Integer`, `String`, etc.) that will replace the placeholder.

In the image example, `ArrayList<Integer>` means that the `ArrayList` can hold only `Integer` objects. The generic type parameter `<Integer>` restricts the types of elements that can be added to the list. This ensures **type safety**, as you won't be able to add any objects of a different type (like a `String`) to that `ArrayList`.

If you don’t provide a type (for example, just `ArrayList` without the `<Integer>`), the compiler will allow any type of object to be added. However, this leads to **type safety issues**, which generics aim to prevent. Using raw types (i.e., without specifying the type parameter) can result in runtime errors because it doesn't enforce the type constraints at compile time.

---

### Example with Generics: 

```java
// Without Generics
ArrayList list = new ArrayList(); // Raw type
list.add("String"); // OK
list.add(123); // OK

// With Generics
ArrayList<Integer> list = new ArrayList<>();
list.add(123); // OK
list.add("String"); // Compile-time error, type safety ensured
```

In the example above, using `ArrayList<Integer>` ensures that only `Integer` values can be added to the list, providing **compile-time type checking**. If you attempt to add a `String` to the list, the compiler will throw an error, preventing potential runtime errors.

---

### Conclusion

Generics offer significant advantages, including:
1. **Code Reusability**: You can write a single class or method that works with different types without rewriting it for each specific type.
2. **Type Safety**: Generics enable stronger type checks at compile time, helping you catch errors early and preventing `ClassCastException` at runtime.
3. **Cleaner Code**: With generics, your code becomes cleaner and easier to maintain, as it eliminates the need for casting.

In summary, generics provide a mechanism for writing flexible, reusable, and type-safe code, which is especially useful when dealing with collections like `ArrayList`. The use of generics helps enforce type safety while avoiding the need to write multiple versions of the same code for different data types.


### Object Cloning in Java

Object cloning in Java is a process of creating an exact copy (clone) of an existing object. It is useful when you need a new object that has the same properties (or state) as an existing one without having to write code to manually copy each field.

Java provides a built-in mechanism for cloning objects through the `clone()` method in the `Object` class. However, cloning is not straightforward and requires some setup, including implementing the `Cloneable` interface and properly overriding the `clone()` method.

### Steps to Clone an Object in Java:

1. **Implement the `Cloneable` Interface**:  
   The class whose objects need to be cloned must implement the `Cloneable` interface. This is a marker interface (i.e., it has no methods) used to signal that the `clone()` method can be called on objects of that class. If a class does not implement `Cloneable` and you call `clone()`, a `CloneNotSupportedException` will be thrown.

2. **Override the `clone()` Method**:  
   The `clone()` method is inherited from the `Object` class, but you usually need to override it in your class to make it `public` and to provide any additional logic if necessary.

3. **Use the `clone()` Method**:  
   Once the class is properly set up, you can call the `clone()` method on an object to create a copy of it.

### Example: Cloning in Java

Here’s a basic example to demonstrate object cloning:

```java
class Human implements Cloneable {
    int age;
    String name;

    // Constructor to initialize the object
    public Human(int age, String name) {
        this.age = age;
        this.name = name;
    }

    // Overriding the clone() method to make it public and handle CloneNotSupportedException
    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone(); // Call the clone() method of Object class
    }

    // Method to display details
    public void display() {
        System.out.println("Age: " + age + ", Name: " + name);
    }
}

public class Main {
    public static void main(String[] args) {
        try {
            // Creating an object of Human
            Human kunal = new Human(34, "Kunal Kushwaha");
            
            // Cloning the object
            Human twin = (Human) kunal.clone();

            // Displaying details of both objects
            System.out.println("Original Object:");
            kunal.display(); // Age: 34, Name: Kunal Kushwaha
            
            System.out.println("Cloned Object:");
            twin.display();  // Age: 34, Name: Kunal Kushwaha

            // Modifying the cloned object to see if it affects the original
            twin.age = 25;
            twin.name = "Twin Kunal";
            
            System.out.println("After modifying the cloned object:");
            System.out.println("Original Object:");
            kunal.display(); // Age: 34, Name: Kunal Kushwaha
            System.out.println("Cloned Object:");
            twin.display();  // Age: 25, Name: Twin Kunal
            
        } catch (CloneNotSupportedException e) {
            e.printStackTrace();
        }
    }
}
```

### Output:

```
Original Object:
Age: 34, Name: Kunal Kushwaha
Cloned Object:
Age: 34, Name: Kunal Kushwaha
After modifying the cloned object:
Original Object:
Age: 34, Name: Kunal Kushwaha
Cloned Object:
Age: 25, Name: Twin Kunal
```

### Key Concepts:

1. **Shallow Cloning**:  
   The example above demonstrates **shallow cloning**, where fields of primitive types (`int`, `float`, etc.) and immutable objects (like `String`) are copied directly. However, for reference types (like arrays or objects), shallow cloning only copies the reference and **does not create a new object for mutable fields**. This means that the original and cloned objects will share the same reference for those fields.
![[Screenshot 2024-10-16 210501.png]]
2. **Deep Cloning**:  
   In **deep cloning**, not only the object itself is cloned, but also the objects referenced by the fields. This ensures that changes to the cloned object do not affect the original object, even for mutable fields. You can implement deep cloning by overriding the `clone()` method to manually clone all the mutable fields.
   ![[Screenshot 2024-10-16 210739.png]]

### Example of Shallow Cloning vs. Deep Cloning

Consider a class that has a reference to an array:

```java
class Person implements Cloneable {
    String name;
    int[] scores;

    public Person(String name, int[] scores) {
        this.name = name;
        this.scores = scores;
    }

    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone(); // Shallow cloning
    }
}

public class Main {
    public static void main(String[] args) throws CloneNotSupportedException {
        int[] scores = {90, 80, 70};
        Person john = new Person("John", scores);
        
        // Shallow clone
        Person johnClone = (Person) john.clone();

        System.out.println("Before modifying scores:");
        System.out.println("John's scores: " + john.scores[0]);
        System.out.println("JohnClone's scores: " + johnClone.scores[0]);

        // Modify the array in the cloned object
        johnClone.scores[0] = 100;

        System.out.println("After modifying scores:");
        System.out.println("John's scores: " + john.scores[0]);        // John's scores will change to 100
        System.out.println("JohnClone's scores: " + johnClone.scores[0]); // JohnClone's scores will also be 100
    }
}
```

#### Output:
```
Before modifying scores:
John's scores: 90
JohnClone's scores: 90
After modifying scores:
John's scores: 100
JohnClone's scores: 100
```

In the example above, both the original `john` object and the cloned `johnClone` share the same reference to the `scores` array. When you modify the array in one object, it affects both because of **shallow cloning**.

### Implementing Deep Cloning:

To achieve **deep cloning**, we need to manually clone mutable fields like arrays or objects inside the `clone()` method:

```java
@Override
protected Object clone() throws CloneNotSupportedException {
    // First, perform a shallow copy
    Person cloned = (Person) super.clone();

    // Now, deep clone the scores array
    cloned.scores = scores.clone();

    return cloned;
}
```

This will ensure that the `scores` array is also cloned, so changes in the cloned object do not affect the original object.

### Conclusion:
- **Shallow Cloning**: Only the object is copied, while references to other objects are shared between the original and cloned object.
- **Deep Cloning**: Both the object and its referenced objects are copied, creating independent objects with no shared references.

Cloning is useful when you need to create copies of objects, but be mindful of whether you need shallow or deep cloning, depending on the structure of your object and the presence of mutable fields.