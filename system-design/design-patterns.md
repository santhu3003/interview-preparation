
# Design Patterns in Java
---

## Why Design Patterns Are Important

✅ Promote code reusability and maintainability  
✅ Make code flexible and scalable to changes  
✅ Improve readability and team collaboration through well-known structures  
✅ Help avoid code duplication and tight coupling  
✅ Are proven solutions to recurring design problems  

---

### 1️⃣ Singleton Pattern

**Description:**  
Ensures a class has only one instance and provides a global point of access to it.  
Used when exactly one object is needed to coordinate actions across a system (like a shared resource).  
It controls instance creation using a private constructor and a static access method.

```java
class Singleton {
    private static Singleton instance;
    private Singleton() {}
    public static Singleton getInstance() {
        if (instance == null) instance = new Singleton();
        return instance;
    }
}
```
**Example Use:** Database connection manager, logger, or configuration settings.

---

### 🏭 2️⃣ Factory Method Pattern

**Description:**  
Defines an interface for creating objects, but allows subclasses to decide which class to instantiate.  
It promotes loose coupling by abstracting the object creation logic away from the client.  
Useful when the creation process is complex or depends on input parameters.

```java
interface Shape { void draw(); }
class Circle implements Shape { public void draw() { System.out.println("Circle"); } }
class ShapeFactory {
    public Shape getShape(String type) {
        if (type.equalsIgnoreCase("circle")) return new Circle();
        return null;
    }
}
```
**Example Use:** Document or UI element creation, where object type depends on configuration.

---

### 🧱 3️⃣ Facade Pattern

**Description:**  
Provides a unified and simplified interface to a complex subsystem of classes.  
It shields clients from the subsystem’s complexity, making the system easier to use.  
Often used to wrap legacy systems or complex libraries.

```java
class CPU { void start() { System.out.println("CPU start"); } }
class Memory { void load() { System.out.println("Memory load"); } }
class ComputerFacade {
    private CPU cpu = new CPU();
    private Memory mem = new Memory();
    void startComputer() { cpu.start(); mem.load(); }
}
```
**Example Use:** Starting a computer, initializing a gaming engine, or media player setup.

---

### 🧠 4️⃣ Strategy Pattern

**Description:**  
Defines a family of algorithms, encapsulates each one, and makes them interchangeable at runtime.  
It allows behavior of an object to change dynamically without modifying the object’s code.  
Promotes the Open/Closed Principle — open for extension, closed for modification.

```java
interface Payment { void pay(); }
class CardPayment implements Payment { public void pay() { System.out.println("Card payment"); } }
class PayPalPayment implements Payment { public void pay() { System.out.println("PayPal payment"); } }
class ShoppingCart {
    Payment payment;
    void setPayment(Payment p) { payment = p; }
    void checkout() { payment.pay(); }
}
```
**Example Use:** Payment methods, sorting algorithms, or compression strategies.

---

### 👀 5️⃣ Observer Pattern

**Description:**  
Establishes a one-to-many relationship so that when one object (subject) changes state, all dependents (observers) are notified.  
It helps implement event-driven systems and promotes loose coupling between objects.  
Observers can subscribe/unsubscribe dynamically.

```java
interface Observer { void update(); }
class Subject {
    List<Observer> obs = new ArrayList<>();
    void add(Observer o) { obs.add(o); }
    void notifyAllObs() { obs.forEach(Observer::update); }
}
class User implements Observer { public void update() { System.out.println("Got notification"); } }
```
**Example Use:** GUI components, news feed updates, or event systems.

---

### 🏗️ 6️⃣ Builder Pattern

**Description:**  
Separates complex object construction from its representation so the same construction process can create different forms.  
It avoids telescoping constructors (too many parameters) and improves readability.  
Useful when creating objects with many optional attributes.

```java
class Burger {
    private String bread, meat, sauce;
    static class Builder {
        Burger b = new Burger();
        Builder bread(String s) { b.bread = s; return this; }
        Builder meat(String s) { b.meat = s; return this; }
        Builder sauce(String s) { b.sauce = s; return this; }
        Burger build() { return b; }
    }
}
```
**Example Use:** Building configuration objects, documents, or complex UI components.

---

### 🔌 7️⃣ Adapter Pattern

**Description:**  
Allows incompatible interfaces to work together by acting as a bridge between them.  
It converts the interface of one class into another interface that a client expects.  
Used when integrating legacy systems or third-party APIs.

```java
interface MediaPlayer { void play(String file); }
class OldPlayer { void playFile(String file) { System.out.println("Playing " + file); } }
class Adapter implements MediaPlayer {
    OldPlayer old = new OldPlayer();
    public void play(String file) { old.playFile(file); }
}
```
**Example Use:** Connecting new software to old libraries or APIs with different interfaces.

---

### 🧩 8️⃣ MVC Pattern (Model–View–Controller)

**Description:**  
Separates an application into three interconnected components — Model (data), View (UI), and Controller (logic).  
This separation improves organization, testability, and scalability.  
Commonly used in web frameworks and GUI applications.

```java
class Model { String data = "Hello"; }
class View { void show(String data) { System.out.println(data); } }
class Controller {
    Model m; View v;
    Controller(Model m, View v) { this.m = m; this.v = v; }
    void updateView() { v.show(m.data); }
}
```
**Example Use:** Spring MVC, web apps, or desktop GUI programs.