![[Pasted image 20241020221335.png]]![[Pasted image 20241020221338.png]]
In Java, **`enum`** (short for "enumeration") is a special data type that represents a group of constants. Enums are used when you need to define a fixed set of known values for a variable, such as the days of the week, months of the year, directions (north, south, east, west), etc.

### Key Features of Enum in Java:
1. **Type-Safety**: Enums provide a type-safe way to define a collection of constants.
2. **Constants**: The values inside an enum are constants, meaning they are implicitly `public`, `static`, and `final`.
3. **Predefined Set of Values**: Enums allow only predefined values (as declared in the enum class) to be assigned to a variable.
4. **Enum Class**: Every enum implicitly extends `java.lang.Enum` class and cannot extend any other class.
5. **Methods in Enum**: Enums can have fields, constructors, and methods like regular classes, but the constructor is private or default (cannot be public or protected).

### Example from the Image:

```java
enum Week {
    Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday;
    
    Week() {
        System.out.println("Constructor called for " + this);
    }
}
```

This example defines an enum called `Week` that represents the days of the week. The constants `Monday`, `Tuesday`, etc., are enum values.

#### Explanation:
- **Enum Values**: The values `Monday`, `Tuesday`, etc., are constants, and they are `public static final` members of the `Week` enum. Since they are `final`, no child enums can be created from them.
  
- **Constructor**: The `Week` enum has a constructor that is private or default (no `public` or `protected` access modifier). This constructor is invoked for each constant when the enum is initialized. The constructor prints a message indicating which constant is being created (e.g., "Constructor called for Monday").

- **Enum constants as objects**: Internally, each constant in the enum is represented as an instance of the enum class, so `public static final Week Monday = new Week();` is called during initialization, which invokes the constructor.

### Code in the Main Class (First Image):

```java
public static void main(String[] args) {
    Week week;
    week = Week.Monday;

    for (Week day : Week.values()) {
        System.out.println(day);
    }

    System.out.println(week.ordinal());
}
```

#### Explanation:
1. **Enum Assignment**: 
   ```java
   week = Week.Monday;
   ```
   This assigns the constant `Monday` from the `Week` enum to the `week` variable. Since enums are type-safe, the `week` variable can only be assigned one of the values from the `Week` enum.

2. **Iterating over Enum Values**:
   ```java
   for (Week day : Week.values()) {
       System.out.println(day);
   }
   ```
   The `Week.values()` method returns an array of all enum constants, allowing you to iterate over them. In the loop, each constant is printed out. This method is useful for getting all possible values of the enum.

3. **Ordinal Method**:
   ```java
   System.out.println(week.ordinal());
   ```
   The `ordinal()` method returns the position of the enum constant in the declaration (starting from 0). So for `Week.Monday`, `ordinal()` will return `0`, since it is the first constant declared.

### Summary of Key Points:
- **Enum constructors**: These are called once for each constant when the enum is loaded. Enum constructors cannot be public.
- **Enum values**: Each constant is an instance of the enum class and is final.
- **Iteration**: The `values()` method allows iteration over all enum constants.
- **Ordinal**: This method provides the index of the constant.

Enums provide a way to create sets of related constants with added functionality, and they can behave like full-fledged classes with methods and fields.