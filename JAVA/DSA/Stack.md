Here's a detailed explanation for `Stack` in Java, similar to the `HashMap` explanation.

## Stack in Java

In Java, `Stack` is a class from the `java.util` package that implements a last-in-first-out (LIFO) data structure. It extends the `Vector` class and provides methods to manipulate the elements in the stack, such as pushing and popping elements.

### Creating a Stack
To create a `Stack`, you simply declare it using the `Stack` class.
```java
import java.util.Stack;

Stack<Integer> stack = new Stack<>();
```

### Common Methods of Stack

1. **Push**: Add an element to the top of the stack.
    ```java
    stack.push(10);
    stack.push(20);
    stack.push(30);
    ```
    
2. **Pop**: Remove and return the top element from the stack.
    ```java
    int topElement = stack.pop();  // Removes and returns 30
    ```
   
3. **Peek**: Retrieve (without removing) the top element of the stack.
    ```java
    int topElement = stack.peek();  // Returns 20 (top element)
    ```

4. **Check if Empty**: Verify whether the stack is empty or not.
    ```java
    boolean isEmpty = stack.isEmpty();  // Returns false (not empty)
    ```

5. **Search**: Find the position of an element in the stack (1-based index).
    ```java
    int position = stack.search(20);  // Returns 1 (top of the stack)
    ```

### Example of Basic Stack Operations
Here’s an example that demonstrates how to use a `Stack` in Java:

```java
import java.util.Stack;

public class StackExample {
    public static void main(String[] args) {
        // Create a Stack of integers
        Stack<Integer> stack = new Stack<>();
        
        // Push elements to the stack
        stack.push(10);
        stack.push(20);
        stack.push(30);
        System.out.println("Stack after pushes: " + stack);
        
        // Pop the top element
        int poppedElement = stack.pop();
        System.out.println("Popped element: " + poppedElement);
        System.out.println("Stack after pop: " + stack);
        
        // Peek the top element
        int topElement = stack.peek();
        System.out.println("Top element: " + topElement);
        
        // Check if the stack is empty
        boolean isEmpty = stack.isEmpty();
        System.out.println("Is stack empty? " + isEmpty);
        
        // Search for an element in the stack
        int position = stack.search(20);
        System.out.println("Position of 20: " + position);
    }
}
```

### Output:
```
Stack after pushes: [10, 20, 30]
Popped element: 30
Stack after pop: [10, 20]
Top element: 20
Is stack empty? false
Position of 20: 1
```

### Explanation:
1. **Push**: Adds elements `10`, `20`, and `30` to the stack.
2. **Pop**: Removes `30` (the topmost element).
3. **Peek**: Retrieves the new top element (`20`) without removing it.
4. **isEmpty**: Returns `false` because the stack still has elements.
5. **Search**: Finds the position of `20` from the top of the stack, which is `1`.

### Checking the Size of the Stack
To check how many elements are in the stack, you can use:
```java
int size = stack.size();
System.out.println("Size of stack: " + size);
```

### Iterating Over Stack
You can iterate over the stack in the following ways:

- **Using a For-Each loop**:
    ```java
    for (Integer element : stack) {
        System.out.println(element);
    }
    ```
    
- **Using a traditional `for` loop**:
    ```java
    for (int i = 0; i < stack.size(); i++) {
        System.out.println(stack.get(i));
    }
    ```

### Advantages of Stack

- **LIFO Structure**: Useful for algorithms that require last-in-first-out ordering like depth-first search (DFS), undo operations in software, or parsing expressions.
- **Easy to Use**: Java's `Stack` class provides an easy way to manipulate stacks without needing to manually implement the stack data structure.

### Disadvantages
- **Legacy Class**: `Stack` is part of Java's older collection classes. Consider using `Deque` (with `ArrayDeque`) as a better-performing stack replacement in some cases.

### Example: Balanced Parentheses Check using Stack

```java
import java.util.Stack;

public class BalancedParentheses {
    public static boolean isBalanced(String str) {
        Stack<Character> stack = new Stack<>();
        
        for (char c : str.toCharArray()) {
            if (c == '(') {
                stack.push(c);
            } else if (c == ')') {
                if (stack.isEmpty()) {
                    return false;
                }
                stack.pop();
            }
        }
        return stack.isEmpty();
    }

    public static void main(String[] args) {
        String str = "(())()";
        System.out.println("Is balanced? " + isBalanced(str));  // Output: true
    }
}
```

### Explanation:
- The `isBalanced` method uses a stack to check if the parentheses are balanced in a string. It pushes opening parentheses onto the stack and pops when a closing parenthesis is found. If the stack is empty at the end, the parentheses are balanced.

### Summary
- `Stack` in Java provides an easy-to-use LIFO data structure.
- Methods like `push`, `pop`, `peek`, `isEmpty`, and `search` make stack operations straightforward.
- Though `Stack` is a legacy class, it’s still used for basic stack-based operations and can be helpful in scenarios requiring LIFO behavior. However, for better performance, consider using `Deque`.

If you have more specific requirements, let me know!