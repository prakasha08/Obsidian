Here's a Java implementation of **OOP concepts in a chess game**:

---

### **1. Encapsulation** (Data Hiding)

Each **chess piece** has its own **color** and **position**, which are kept private. Getters and setters allow controlled access.

```java
abstract class Piece {
    private String color;
    private int x, y; // Position on the board

    public Piece(String color, int x, int y) {
        this.color = color;
        this.x = x;
        this.y = y;
    }

    public String getColor() {
        return color;
    }

    public int getX() {
        return x;
    }

    public int getY() {
        return y;
    }

    public void setPosition(int x, int y) {
        this.x = x;
        this.y = y;
    }

    // Abstraction: Enforcing move behavior in all pieces
    abstract void move(int newX, int newY);
}
```

---

### **2. Inheritance** (Reusability)

Different pieces inherit from the **`Piece`** class and define their own movement.

```java
class Knight extends Piece {
    public Knight(String color, int x, int y) {
        super(color, x, y);
    }

    @Override
    void move(int newX, int newY) {
        System.out.println("Knight moves in L-shape to (" + newX + ", " + newY + ")");
    }
}

class Bishop extends Piece {
    public Bishop(String color, int x, int y) {
        super(color, x, y);
    }

    @Override
    void move(int newX, int newY) {
        System.out.println("Bishop moves diagonally to (" + newX + ", " + newY + ")");
    }
}
```

---

### **3. Polymorphism** (Dynamic Behavior)

A method accepts any **piece** and executes its move dynamically.

```java
public class ChessGame {
    public static void movePiece(Piece piece, int newX, int newY) {
        piece.move(newX, newY);  // Calls the overridden method
        piece.setPosition(newX, newY);
    }

    public static void main(String[] args) {
        Piece knight = new Knight("White", 2, 1);
        Piece bishop = new Bishop("Black", 4, 4);

        movePiece(knight, 3, 3);  // Calls Knight's move method
        movePiece(bishop, 6, 6);  // Calls Bishop's move method
    }
}
```

---

### **4. Abstraction** (Hiding Details)

- The **`Piece`** class enforces a **`move()`** method without revealing its implementation.
- The **player** does not need to know the internal movement logic.

---

### **Output**

```
Knight moves in L-shape to (3, 3)
Bishop moves diagonally to (6, 6)
```

---

### **Summary**

✅ **Encapsulation**: Attributes like `color` and `position` are private.  
✅ **Inheritance**: Knight and Bishop inherit from `Piece`.  
✅ **Polymorphism**: `movePiece()` handles all piece types dynamically.  
✅ **Abstraction**: `move()` is an abstract method ensuring implementation by subclasses.

---

This makes the chess game **modular, reusable, and easy to extend**! 🏆 Let me know if you need improvements! 🚀