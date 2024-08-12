
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