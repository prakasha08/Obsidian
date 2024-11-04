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
   ![[Pasted image 20241016210506.png]]
   ![[Pasted image 20241016210402.png]]

2. **Deep Cloning**:  
   In **deep cloning**, not only the object itself is cloned, but also the objects referenced by the fields. This ensures that changes to the cloned object do not affect the original object, even for mutable fields. You can implement deep cloning by overriding the `clone()` method to manually clone all the mutable fields.
![[Pasted image 20241016210749.png]]
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