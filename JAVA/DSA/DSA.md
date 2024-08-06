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
empIds.put("John", 98765); System.out.println(empIds);//johnid changed to 98765
empIds.replace("Kramer", 777); System.out.println(empIds);//if found replace
empIds.putIfAbsent("Steve", 222); System.out.println(empIds);//add if adsent
empIds.remove("Steve"); System.out.println(empIds);
```

![[Pasted image 20240806183732.png]]
***If you want print the overall map follow below
![[Pasted image 20240806183822.png]]
another way to whole is 
![[Pasted image 20240806184652.png]]