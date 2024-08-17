 
# HashMap
In Java, a `HashMap` is a part of the Java Collections Framework and is used to store key-value(always in wrapper class like Integer,Float not primitives int,float) pairs. It's a map-based collection that allows you to store and retrieve values based on keys. Here are some key properties and how to use a `HashMap`:
#### Creating a `HashMap`
```java
HashMap<String, Integer> map = new HashMap<>();
```
#### Adding Elements
```java
map.put("Apple", 1); map.put("Banana", 2); map.put("Cherry", 3);
```

```java
HashSet<String> set1 = new HashSet<>(); set1.add("Element1"); set1.add("Element2"); set1.add("Element3"); // Create the second HashSet HashSet<String> set2 = new HashSet<>(); // Copy elements from set1 to set2 set2.addAll(set1);
```
#### Accessing Elements
```java
int value = map.get("Apple"); // Returns 1
```
#### Checking for Key/Value
```java
boolean hasKey = map.containsKey("Banana"); // Returns true
boolean hasValue = map.containsValue(3);    // Returns true
```
#### Removing Elements
```java
map.remove("Cherry");
```
#### Iterating Over Elements
```java
 //Using keySet() 
 for (String key : map.keySet()) {     System.out.println(key + ": " + map.get(key)); } 
 
 //Using entrySet() 
 for (Map.Entry<String, Integer> entry : map.entrySet()) {     System.out.println(entry.getKey() + ": " + entry.getValue()); }`
```

#### Size of the Map
```java
int size = map.size(); // Returns the number of key-value pairs`
```
#### Clearing the Map
```java
map.clear(); // Removes all key-value pairs`
```
#### Example
```java
import java.util.HashMap;
import java.util.Map;

public class HashMapExample {
    public static void main(String[] args) {
        HashMap<String, Integer> map = new HashMap<>();
        
        // Adding elements
        map.put("Apple", 1);
        map.put("Banana", 2);
        map.put("Cherry", 3);
        
        // Accessing elements
        System.out.println("Apple: " + map.get("Apple"));
        
        // Checking for key/value
        System.out.println("Contains Banana? " + map.containsKey("Banana"));
        System.out.println("Contains value 3? " + map.containsValue(3));
        
        // Removing an element
        map.remove("Cherry");
        
        // Iterating over elements
        for (Map.Entry<String, Integer> entry : map.entrySet()) {
            System.out.println(entry.getKey() + ": " + entry.getValue());
        }
        
        // Size and clearing
        System.out.println("Size: " + map.size());
        map.clear();
        System.out.println("Size after clearing: " + map.size());
    }
}

```

```java
HashMap<String, Integer> empIds = new HashMap<>();
empIds.put("John", 12345); empIds.put("Carl", 54321); empIds.put("Jerry", 8675309);
System.out.println(empIds);
System.out.println(empIds.get("Carl"));
System.out.println(empIds.containsKey("George"));//false
System.out.println(empIds.containsValue (8675309));//true
empIds.put("John", 98765);
System.out.println(empIds);//johnid changed to 98765
empIds.replace("Kramer", 777);
System.out.println(empIds);//if found replace
empIds.putIfAbsent("Steve", 222); 
System.out.println(empIds);//add if adsent
empIds.remove("Steve");
System.out.println(empIds);
```

![[Pasted image 20240806183732.png]]
***If you want print the overall map follow below
![[Pasted image 20240806183822.png]]
another way to whole is 
![[Pasted image 20240806184652.png]]

## getOrDefault

The `getOrDefault` method in Java is part of the `Map` interface and is available from Java 8 onwards. It is used to retrieve the value associated with a specified key in a map. If the key is not present in the map, `getOrDefault` returns a specified default value instead of `null`. This method provides a concise and readable way to handle cases where a key might not be present in the map.

### Syntax

```java
V getOrDefault(Object key, V defaultValue)
```

- **key**: The key whose associated value is to be returned.
- **defaultValue**: The value to be returned if the key is not found in the map.

### Example

Here's a practical example to illustrate the usage of `getOrDefault`:

```java
import java.util.HashMap;
import java.util.Map;

public class Main {
    public static void main(String[] args) {
        // Create a HashMap and populate it with some values
        Map<String, Integer> fruitMap = new HashMap<>();
        fruitMap.put("Apple", 10);
        fruitMap.put("Banana", 20);
        fruitMap.put("Orange", 30);
        
        // Using getOrDefault to retrieve values
        System.out.println("Apple count: " + fruitMap.getOrDefault("Apple", 0)); // Output: 10
        System.out.println("Banana count: " + fruitMap.getOrDefault("Banana", 0)); // Output: 20
        System.out.println("Grapes count: " + fruitMap.getOrDefault("Grapes", 0)); // Output: 0
        
        // Using getOrDefault to handle a missing key with a default value
        System.out.println("Pineapple count: " + fruitMap.getOrDefault("Pineapple", 5)); // Output: 5
    }
}
```

### Explanation

1. **Initialization**: A `HashMap` named `fruitMap` is created and populated with some fruit names as keys and their counts as values.
2. **Using `getOrDefault`**:
   - `fruitMap.getOrDefault("Apple", 0)`: Since "Apple" is present in the map with a count of 10, the method returns 10.
   - `fruitMap.getOrDefault("Banana", 0)`: Since "Banana" is present in the map with a count of 20, the method returns 20.
   - `fruitMap.getOrDefault("Grapes", 0)`: Since "Grapes" is not present in the map, the method returns the default value 0.
   - `fruitMap.getOrDefault("Pineapple", 5)`: Since "Pineapple" is not present in the map, the method returns the default value 5.

### Advantages of `getOrDefault`

- **Readability**: The method provides a clear and concise way to handle missing keys without needing additional checks.
- **Default Value**: It allows you to specify a default value directly, making the code cleaner and more maintainable.
- **Null Handling**: It helps avoid `NullPointerException` by providing a default value when the key is not found.

### Summary

The `getOrDefault` method is a useful addition to the `Map` interface that simplifies handling cases where a key might not be present. It enhances code readability and reduces the need for explicit null checks, making it a valuable tool in any Java programmer's toolkit.
# HashSet

In Java, a `HashSet` is a part of the Java Collections Framework and implements the `Set` interface. It is used to store unique elements and does not maintain any specific order. It is backed by a `HashMap`, which provides constant-time performance for basic operations like add, remove, and contains.

#### **Creating a `HashSet`**
```java
HashSet<Integer> set = new HashSet<>();
```

#### **Adding Elements**
```java
set.add(5);
set.add(3);
set.add(7);
```

#### **Accessing Elements**
- `HashSet` does not provide methods to access elements by index since it does not maintain order.

#### **Checking for Element**
```java
boolean contains = set.contains(3); // Returns true
```

#### **Removing Elements**
```java
set.remove(7);
```

#### **Iterating Over Elements**
```java
// Using enhanced for-loop
for (Integer num : set) {
    System.out.println(num);
}
```

#### **Size of the Set**
```java
int size = set.size(); // Returns the number of elements
```

#### **Clearing the Set**
```java
set.clear(); // Removes all elements
```

#### **Example**
```java
import java.util.HashSet;

public class HashSetExample {
    public static void main(String[] args) {
        HashSet<Integer> set = new HashSet<>();
        
        // Adding elements
        set.add(5);
        set.add(3);
        set.add(7);
        
        // Checking for element
        System.out.println("Contains 3? " + set.contains(3));
        
        // Removing an element
        set.remove(7);
        
        // Iterating over elements
        for (Integer num : set) {
            System.out.println(num);
        }
        
        // Size and clearing
        System.out.println("Size: " + set.size());
        set.clear();
        System.out.println("Size after clearing: " + set.size());
    }
}
```

---

# TreeSet

In Java, a `TreeSet` is a part of the Java Collections Framework and implements the `NavigableSet` interface. It is used to store elements in a sorted order. The `TreeSet` uses a `TreeMap` to maintain the order of elements.

#### **Creating a `TreeSet`**
```java
TreeSet<Integer> set = new TreeSet<>();
```

#### **Adding Elements**
```java
set.add(5);
set.add(3);
set.add(7);
```

#### **Accessing Elements**
- Like `HashSet`, `TreeSet` does not allow direct access by index but maintains sorted order.

#### **Checking for Element**
```java
boolean contains = set.contains(3); // Returns true
```

#### **Removing Elements**
```java
set.remove(7);
```

#### **Iterating Over Elements**
```java
// Using enhanced for-loop
for (Integer num : set) {
    System.out.println(num);
}
```

#### **Size of the Set**
```java
int size = set.size(); // Returns the number of elements
```

#### **Clearing the Set**
```java
set.clear(); // Removes all elements
```

#### **Example**
```java
import java.util.TreeSet;

public class TreeSetExample {
    public static void main(String[] args) {
        TreeSet<Integer> set = new TreeSet<>();
        
        // Adding elements
        set.add(5);
        set.add(3);
        set.add(7);
        
        // Checking for element
        System.out.println("Contains 3? " + set.contains(3));
        
        // Removing an element
        set.remove(7);
        
        // Iterating over elements
        for (Integer num : set) {
            System.out.println(num);
        }
        
        // Size and clearing
        System.out.println("Size: " + set.size());
        set.clear();
        System.out.println("Size after clearing: " + set.size());
    }
}
```

---

# TreeMap

In Java, a `TreeMap` is a part of the Java Collections Framework and implements the `NavigableMap` interface. It is used to store key-value pairs in sorted order based on the natural ordering of the keys or by a specified comparator.

#### **Creating a `TreeMap`**
```java
TreeMap<String, Integer> map = new TreeMap<>();
```

#### **Adding Elements**
```java
map.put("Apple", 1);
map.put("Banana", 2);
map.put("Cherry", 3);
```

#### **Accessing Elements**
```java
int value = map.get("Apple"); // Returns 1
```

#### **Checking for Key/Value**
```java
boolean hasKey = map.containsKey("Banana"); // Returns true
boolean hasValue = map.containsValue(3);    // Returns true
```

#### **Removing Elements**
```java
map.remove("Cherry");
```

#### **Iterating Over Elements**
```java
// Using entrySet()
for (Map.Entry<String, Integer> entry : map.entrySet()) {
    System.out.println(entry.getKey() + ": " + entry.getValue());
}
```

#### **Size of the Map**
```java
int size = map.size(); // Returns the number of key-value pairs
```

#### **Clearing the Map**
```java
map.clear(); // Removes all key-value pairs
```

#### **Example**
```java
import java.util.TreeMap;
import java.util.Map;

public class TreeMapExample {
    public static void main(String[] args) {
        TreeMap<String, Integer> map = new TreeMap<>();
        
        // Adding elements
        map.put("Apple", 1);
        map.put("Banana", 2);
        map.put("Cherry", 3);
        
        // Accessing elements
        System.out.println("Apple: " + map.get("Apple"));
        
        // Checking for key/value
        System.out.println("Contains Banana? " + map.containsKey("Banana"));
        System.out.println("Contains value 3? " + map.containsValue(3));
        
        // Removing an element
        map.remove("Cherry");
        
        // Iterating over elements
        for (Map.Entry<String, Integer> entry : map.entrySet()) {
            System.out.println(entry.getKey() + ": " + entry.getValue());
        }
        
        // Size and clearing
        System.out.println("Size: " + map.size());
        map.clear();
        System.out.println("Size after clearing: " + map.size());
    }
}
```

# Entry

In Java, `Map.Entry` and `entrySet()` are key concepts when working with the `Map` interface, which is part of the Java Collections Framework. Here's a detailed explanation:

### **Map.Entry**

`Map.Entry` is an inner interface of the `Map` interface. It represents a key-value pair (or mapping) in a `Map`. The `Map.Entry` interface provides methods to access the key and value of a map entry.

#### **Key Methods of `Map.Entry`**
- **`getKey()`**: Returns the key corresponding to the entry.
- **`getValue()`**: Returns the value corresponding to the entry.
- **`setValue(V value)`**: Sets the value corresponding to the entry. This method is optional and is typically used when modifying entries in the map.

#### **Example Usage**
```java
import java.util.HashMap;
import java.util.Map;

public class MapEntryExample {
    public static void main(String[] args) {
        Map<String, Integer> map = new HashMap<>();
        map.put("Apple", 1);
        map.put("Banana", 2);
        map.put("Cherry", 3);
        
        // Iterating over map entries
        for (Map.Entry<String, Integer> entry : map.entrySet()) {
            String key = entry.getKey();
            Integer value = entry.getValue();
            System.out.println(key + ": " + value);
        }
    }
}
```

### **entrySet() Method**

The `entrySet()` method is part of the `Map` interface. It returns a `Set<Map.Entry<K, V>>` view of the mappings contained in the map. This set allows you to iterate over the key-value pairs in the map.

#### **Key Points**
- **Returns a Set**: The `entrySet()` method returns a `Set` of `Map.Entry` objects, where each `Map.Entry` represents a key-value pair in the map.
- **Useful for Iteration**: Using `entrySet()` is a common way to iterate over all key-value pairs in a map, especially when you need to access both keys and values.

#### **Example Usage**
```java
import java.util.HashMap;
import java.util.Map;

public class EntrySetExample {
    public static void main(String[] args) {
        Map<String, Integer> map = new HashMap<>();
        map.put("Apple", 1);
        map.put("Banana", 2);
        map.put("Cherry", 3);
        
        // Using entrySet to iterate over map entries
        for (Map.Entry<String, Integer> entry : map.entrySet()) {
            String key = entry.getKey();
            Integer value = entry.getValue();
            System.out.println(key + ": " + value);
        }
    }
}
```

### **Summary**

- **`Map.Entry`**: Represents a key-value pair in a `Map`. Provides methods to access and modify the key and value.
- **`entrySet()`**: Returns a `Set` of `Map.Entry` objects, allowing iteration over key-value pairs in the map.

Using `entrySet()` with `Map.Entry` is particularly useful when you need to work with both keys and values simultaneously, such as when iterating through a map.