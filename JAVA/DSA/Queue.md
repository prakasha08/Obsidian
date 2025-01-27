# Implement Queue Using Linked List
![[Pasted image 20240830184429.png]]

# Deque
A **Deque** (short for "double-ended queue") in Java is a linear data structure that allows the insertion and removal of elements from both ends (front and rear). It is part of the **`java.util`** package and can be implemented using classes like **`ArrayDeque`**, **`LinkedList`**, or **`PriorityQueue`**.

Here’s a detailed explanation of **Deque** in Java and its built-in methods:

---

### **Deque Interface Overview**

- **Package:** `java.util`
- **Interface:** `Deque<E>`
- It extends the **`Queue`** interface.
- It allows elements to be added or removed from both ends of the queue.

**Common Implementations:**

1. **`ArrayDeque`**: Uses a resizable array for storing elements.
2. **`LinkedList`**: Uses a doubly-linked list for storage.

**Key Features:**

- Supports both stack and queue operations.
- Can function as a **FIFO (First-In-First-Out)** queue or **LIFO (Last-In-First-Out)** stack.
- Allows `null` elements in **`LinkedList`**, but not in **`ArrayDeque`**.

---

### **Creating a Deque**

Here’s how to create a Deque:

```java
import java.util.Deque;
import java.util.ArrayDeque;

public class Main {
    public static void main(String[] args) {
        // Creating a Deque using ArrayDeque
        Deque<Integer> deque = new ArrayDeque<>();

        // Adding elements
        deque.addFirst(10); // Add at the front
        deque.addLast(20);  // Add at the rear

        System.out.println(deque); // Output: [10, 20]
    }
}
```

---

### **Built-in Methods in Deque**

The **Deque** interface provides many methods for different operations. They can be grouped based on the operation:

#### **1. Adding Elements**

|**Method**|**Description**|
|---|---|
|`addFirst(E e)`|Adds the specified element at the front of the deque.|
|`addLast(E e)`|Adds the specified element at the end of the deque.|
|`offerFirst(E e)`|Inserts the element at the front; returns `true` if successful, `false` otherwise.|
|`offerLast(E e)`|Inserts the element at the end; returns `true` if successful, `false` otherwise.|
|`push(E e)`|Pushes an element onto the stack represented by the deque (equivalent to `addFirst`).|

---

#### **2. Removing Elements**

|**Method**|**Description**|
|---|---|
|`removeFirst()`|Removes and returns the first element of the deque. Throws exception if empty.|
|`removeLast()`|Removes and returns the last element of the deque. Throws exception if empty.|
|`pollFirst()`|Removes and returns the first element, or `null` if the deque is empty.|
|`pollLast()`|Removes and returns the last element, or `null` if the deque is empty.|
|`pop()`|Removes and returns the element at the front (equivalent to `removeFirst`).|

---

#### **3. Accessing Elements**

|**Method**|**Description**|
|---|---|
|`getFirst()`|Retrieves the first element without removing it. Throws exception if empty.|
|`getLast()`|Retrieves the last element without removing it. Throws exception if empty.|
|`peekFirst()`|Retrieves the first element, or `null` if the deque is empty.|
|`peekLast()`|Retrieves the last element, or `null` if the deque is empty.|

---

#### **4. Iteration**

|**Method**|**Description**|
|---|---|
|`iterator()`|Returns an iterator to traverse the deque from front to back.|
|`descendingIterator()`|Returns an iterator to traverse the deque from back to front.|

---

#### **5. Utility Methods**

|**Method**|**Description**|
|---|---|
|`isEmpty()`|Checks if the deque is empty.|
|`size()`|Returns the number of elements in the deque.|
|`clear()`|Removes all the elements from the deque.|
|`contains(Object o)`|Checks if the deque contains the specified element.|

---

### **Deque as a Stack**

You can use a Deque as a stack (LIFO):

```java
import java.util.Deque;
import java.util.ArrayDeque;

public class Main {
    public static void main(String[] args) {
        Deque<Integer> stack = new ArrayDeque<>();
        stack.push(1); // Push 1
        stack.push(2); // Push 2
        stack.push(3); // Push 3

        System.out.println(stack.pop()); // Remove and return the top (3)
        System.out.println(stack);       // Output: [2, 1]
    }
}
```

---

### **Deque as a Queue**

You can use a Deque as a queue (FIFO):

```java
import java.util.Deque;
import java.util.ArrayDeque;

public class Main {
    public static void main(String[] args) {
        Deque<Integer> queue = new ArrayDeque<>();
        queue.addLast(1); // Add to the rear
        queue.addLast(2); // Add to the rear
        queue.addLast(3); // Add to the rear

        System.out.println(queue.pollFirst()); // Remove and return the front (1)
        System.out.println(queue);            // Output: [2, 3]
    }
}
```

---

### **Advantages of Deque**

1. Flexibility to operate as both a stack and a queue.
2. Efficient performance for both insertion and deletion (O(1) for both ends).

### **Use Cases of Deque**

1. **Sliding Window Problems**: Optimizing performance when maintaining a window of data.
2. **Undo Operations**: Storing operations for undo-redo functionality.
3. **Palindrome Checking**: Comparing elements from both ends.
4. **Stack Implementations**: When resizable storage is needed.

Let me know if you'd like specific examples for any of these methods or use cases!
# Priority Queue

A `PriorityQueue` is a part of the Java Collections Framework and is used to store elements where each element has a priority. The elements with higher priority are served before elements with lower priority. By default, it is a min-heap (smallest element is at the front).

#### Creating a `PriorityQueue`
```java
PriorityQueue<Integer> minHeap = new PriorityQueue<>();
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
```

#### Adding Elements
```java
minHeap.add(10);
minHeap.add(20);
minHeap.add(15);

maxHeap.add(10);
maxHeap.add(20);
maxHeap.add(15);
```

#### Accessing the Top Element
```java
int minTop = minHeap.peek(); // Returns the smallest element
int maxTop = maxHeap.peek(); // Returns the largest element
```

#### Removing Elements
```java
minHeap.poll(); // Removes and returns the smallest element
maxHeap.poll(); // Removes and returns the largest element
```

#### Iterating Over Elements
```java
for (int num : minHeap) {
    System.out.println(num); // Order is not guaranteed
}

for (int num : maxHeap) {
    System.out.println(num); // Order is not guaranteed
}
```

#### Size of the Queue
```java
int minSize = minHeap.size(); // Returns the number of elements
int maxSize = maxHeap.size(); // Returns the number of elements
```

#### Clearing the Queue
```java
minHeap.clear(); // Removes all elements
maxHeap.clear(); // Removes all elements
```

#### Example
```java
import java.util.Collections;
import java.util.PriorityQueue;

public class PriorityQueueExample {
    public static void main(String[] args) {
        PriorityQueue<Integer> minHeap = new PriorityQueue<>();
        PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
        
        // Adding elements
        minHeap.add(10);
        minHeap.add(20);
        minHeap.add(15);

        maxHeap.add(10);
        maxHeap.add(20);
        maxHeap.add(15);
        
        // Accessing the top element
        System.out.println("Min-Heap top element: " + minHeap.peek());
        System.out.println("Max-Heap top element: " + maxHeap.peek());
        
        // Removing elements
        System.out.println("Removing from Min-Heap: " + minHeap.poll());
        System.out.println("Removing from Max-Heap: " + maxHeap.poll());
        
        // Iterating over elements
        System.out.println("Min-Heap elements:");
        for (int num : minHeap) {
            System.out.println(num);
        }

        System.out.println("Max-Heap elements:");
        for (int num : maxHeap) {
            System.out.println(num);
        }
        
        // Size and clearing
        System.out.println("Min-Heap size: " + minHeap.size());
        minHeap.clear();
        System.out.println("Min-Heap size after clearing: " + minHeap.size());
        
        System.out.println("Max-Heap size: " + maxHeap.size());
        maxHeap.clear();
        System.out.println("Max-Heap size after clearing: " + maxHeap.size());
    }
}
```

### Example with Custom Comparator
```java
import java.util.Comparator;
import java.util.PriorityQueue;

public class CustomComparatorExample {
    public static void main(String[] args) {
        // Custom comparator for max-heap
        PriorityQueue<Integer> customHeap = new PriorityQueue<>(new Comparator<Integer>() {
            @Override
            public int compare(Integer n1, Integer n2) {
                return n2 - n1; // Reverse order for max-heap
            }
        });
        
        // Adding elements
        customHeap.add(10);
        customHeap.add(20);
        customHeap.add(15);
        
        // Accessing the top element
        System.out.println("Custom Heap top element: " + customHeap.peek());
        
        // Removing elements
        System.out.println("Removing from Custom Heap: " + customHeap.poll());
        
        // Iterating over elements
        System.out.println("Custom Heap elements:");
        for (int num : customHeap) {
            System.out.println(num);
        }
        
        // Size and clearing
        System.out.println("Custom Heap size: " + customHeap.size());
        customHeap.clear();
        System.out.println("Custom Heap size after clearing: " + customHeap.size());
    }
}
```

### Summary

- **PriorityQueue** is used to store elements with associated priorities.
- By default, it is a min-heap, but you can create a max-heap using a custom comparator.
- Common operations include `add`, `peek`, `poll`, `size`, and `clear`.
- Iterating over a `PriorityQueue` does not guarantee any specific order.

This guide should give you a good understanding of how to work with `PriorityQueue` in Java.