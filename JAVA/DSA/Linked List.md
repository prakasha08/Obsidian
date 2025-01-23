![[Pasted image 20240830185410.png]]
### What is a Linked List?

A **linked list** is a linear data structure where elements, called **nodes**, are connected using pointers. Each node contains two parts:

1. **Data**: The value stored in the node.
2. **Next**: A pointer/reference to the next node in the sequence.

Unlike arrays, linked lists do not store elements in contiguous memory locations. Instead, each node is scattered in memory and linked using pointers.

### Types of Linked Lists

1. **Singly Linked List**: Each node points to the next node. The last node points to `null`.
2. **Doubly Linked List**: Each node has two pointers, one pointing to the next node and one to the previous node.
3. **Circular Linked List**: The last node points back to the first node, forming a circle.

---

### Advantages of Linked Lists

- **Dynamic Size**: The size of a linked list can grow or shrink as needed.
- **Efficient Insertions/Deletions**: Adding or removing elements is efficient, especially at the beginning or middle, as it only involves changing pointers.

### Disadvantages

- **Memory Overhead**: Each node requires extra memory for the pointer.
- **Sequential Access**: To access a specific element, you must traverse the list from the head.

---

### Java Implementation of Linked List

#### 1. **Singly Linked List**

Here’s how you can implement a simple singly linked list in Java:

```java
// Node class
class Node {
    int data;
    Node next;

    public Node(int data) {
        this.data = data;
        this.next = null;
    }
}

// Linked List class
class SinglyLinkedList {
    Node head; // Head of the list

    // Add a node at the end
    public void add(int data) {
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
        } else {
            Node current = head;
            while (current.next != null) {
                current = current.next;
            }
            current.next = newNode;
        }
    }

    // Display the linked list
    public void display() {
        Node current = head;
        while (current != null) {
            System.out.print(current.data + " -> ");
            current = current.next;
        }
        System.out.println("null");
    }

    // Delete a node by value
    public void delete(int key) {
        if (head == null) return;

        // If the head node holds the key
        if (head.data == key) {
            head = head.next;
            return;
        }

        Node current = head;
        while (current.next != null && current.next.data != key) {
            current = current.next;
        }

        if (current.next != null) {
            current.next = current.next.next;
        }
    }
}

// Main class to test the implementation
public class Main {
    public static void main(String[] args) {
        SinglyLinkedList list = new SinglyLinkedList();
        list.add(10);
        list.add(20);
        list.add(30);

        System.out.println("Linked List:");
        list.display();

        list.delete(20);
        System.out.println("After deleting 20:");
        list.display();
    }
}
```

#### Output:

```
Linked List:
10 -> 20 -> 30 -> null
After deleting 20:
10 -> 30 -> null
```

---

#### 2. **Doubly Linked List**

```java
// Node class
class DoublyNode {
    int data;
    DoublyNode prev;
    DoublyNode next;

    public DoublyNode(int data) {
        this.data = data;
        this.prev = null;
        this.next = null;
    }
}

// Doubly Linked List class
class DoublyLinkedList {
    DoublyNode head;

    // Add a node at the end
    public void add(int data) {
        DoublyNode newNode = new DoublyNode(data);
        if (head == null) {
            head = newNode;
        } else {
            DoublyNode current = head;
            while (current.next != null) {
                current = current.next;
            }
            current.next = newNode;
            newNode.prev = current;
        }
    }

    // Display the linked list from the front
    public void displayForward() {
        DoublyNode current = head;
        while (current != null) {
            System.out.print(current.data + " -> ");
            current = current.next;
        }
        System.out.println("null");
    }

    // Display the linked list from the end
    public void displayBackward() {
        if (head == null) return;

        DoublyNode current = head;
        while (current.next != null) {
            current = current.next;
        }

        while (current != null) {
            System.out.print(current.data + " -> ");
            current = current.prev;
        }
        System.out.println("null");
    }
}

// Main class to test the implementation
public class Main {
    public static void main(String[] args) {
        DoublyLinkedList list = new DoublyLinkedList();
        list.add(10);
        list.add(20);
        list.add(30);

        System.out.println("Forward:");
        list.displayForward();

        System.out.println("Backward:");
        list.displayBackward();
    }
}
```

#### Output:

```
Forward:
10 -> 20 -> 30 -> null
Backward:
30 -> 20 -> 10 -> null
```

---

### Key Operations in Linked Lists

1. **Add/Insert**: Add a new node at the beginning, middle, or end.
2. **Delete**: Remove a node by value or position.
3. **Search**: Find a node with a specific value.
4. **Traversal**: Move through the list to access or modify data.

Let me know if you'd like more examples or detailed explanations!
```java
import java.util.LinkedList;

public class Main {
    public static void main(String[] args) {
        // Create a LinkedList
        LinkedList<String> list = new LinkedList<>();

        // Add elements
        list.add("Apple");
        list.add("Banana");
        list.add("Cherry");
        System.out.println("Initial LinkedList: " + list);

        // Add at a specific position
        list.add(1, "Blueberry");
        System.out.println("After adding Blueberry: " + list);

        // Add to the beginning
        list.addFirst("Mango");
        System.out.println("After adding Mango at the beginning: " + list);

        // Add to the end
        list.addLast("Orange");
        System.out.println("After adding Orange at the end: " + list);

        // Remove elements
        list.remove("Banana"); // By value
        System.out.println("After removing Banana: " + list);

        list.remove(2); // By index
        System.out.println("After removing element at index 2: " + list);

        list.removeFirst(); // Remove the first element
        System.out.println("After removing the first element: " + list);

        list.removeLast(); // Remove the last element
        System.out.println("After removing the last element: " + list);

        // Access elements
        System.out.println("First element: " + list.getFirst());
        System.out.println("Last element: " + list.getLast());

        // Check if the list contains an element
        System.out.println("Contains 'Cherry': " + list.contains("Cherry"));

        // Get the size of the LinkedList
        System.out.println("Size of LinkedList: " + list.size());

        // Iterate through the LinkedList
        System.out.println("Iterating through LinkedList:");
        for (String item : list) {
            System.out.println(item);
        }
    }
}

```