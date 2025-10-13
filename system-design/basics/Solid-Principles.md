# SOLID Principles in Object-Oriented Design

The SOLID principles are five key guidelines for writing clean, maintainable, and scalable object-oriented code.

---

## 1. **S**ingle Responsibility Principle (SRP)

**Definition:**  
A class should have only one reason to change, meaning it should have only one job or responsibility.

**Example (Java):**
```java
// Handles only user data
class User {
    String name;
    String email;
}

// Handles only user persistence
class UserRepository {
    void save(User user) { /* save logic */ }
}
```

---

## 2. **O**pen/Closed Principle (OCP)

**Definition:**  
Software entities (classes, modules, functions) should be open for extension but closed for modification.

**Example (Java):**
```java
abstract class Shape {
    abstract double area();
}

class Circle extends Shape {
    double radius;
    double area() { return Math.PI * radius * radius; }
}

class Square extends Shape {
    double side;
    double area() { return side * side; }
}
```
*You can add new shapes by extending `Shape` without modifying existing code.*

---

## 3. **L**iskov Substitution Principle (LSP)

**Definition:**  
Subtypes must be substitutable for their base types without altering the correctness of the program.

**Example (Java):**
```java
class Bird {
    void fly() { System.out.println("Flying"); }
}

class Sparrow extends Bird { }

class Ostrich extends Bird {
    // Ostrich can't fly, so this breaks LSP!
    // void fly() { throw new UnsupportedOperationException(); }
}
```
*Design hierarchies so subclasses truly fit the parent type.*

---

## 4. **I**nterface Segregation Principle (ISP)

**Definition:**  
Clients should not be forced to depend on interfaces they do not use.

**Example (Java):**
```java
interface Printer {
    void print();
}

interface Scanner {
    void scan();
}

// Good: separate interfaces for different functionalities
class MultiFunctionPrinter implements Printer, Scanner {
    public void print() { /* ... */ }
    public void scan() { /* ... */ }
}
```

---

## 5. **D**ependency Inversion Principle (DIP)

**Definition:**  
High-level modules should not depend on low-level modules; both should depend on abstractions.

**Example (Java):**
```java
interface Database {
    void save(String data);
}

class MySQLDatabase implements Database {
    public void save(String data) { /* MySQL save logic */ }
}

class DataService {
    private Database db;
    DataService(Database db) { this.db = db; }
    void saveData(String data) { db.save(data); }
}
```
*`DataService` depends on the abstraction (`Database`), not a concrete class.*

---

## Summary Table

| Principle | Purpose                                      | Example Keyword      |
|-----------|----------------------------------------------|----------------------|
| SRP       | One responsibility per class                 | "User" vs "UserRepo" |
| OCP       | Extend, don’t modify                        | `Shape` subclasses   |
| LSP       | Subtypes fit base types                      | `Bird`/`Sparrow`     |
| ISP       | Small, focused interfaces                    | `Printer`, `Scanner` |
| DIP       | Depend on abstractions, not concretions      | `Database` interface |

---