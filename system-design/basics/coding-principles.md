# General Software Design Principles

These principles help you write clean, maintainable, and efficient code.

---

## 1. **KISS** – Keep It Simple, Stupid

**Definition:**  
Favor simple solutions over complex ones. Avoid unnecessary complexity.

**Example (Java):**
```java
// Simple way to sum numbers in a list
int sum(List<Integer> nums) {
    int total = 0;
    for (int n : nums) total += n;
    return total;
}
```

---

## 2. **DRY** – Don’t Repeat Yourself

**Definition:**  
Avoid duplicating code. Extract common logic into reusable functions or classes.

**Example (Java):**
```java
// Instead of duplicating validation logic
boolean isValidEmail(String email) { /* ... */ }
boolean isValidPhone(String phone) { /* ... */ }

// DRY: use a utility class
class Validator {
    static boolean isValidEmail(String email) { /* ... */ }
    static boolean isValidPhone(String phone) { /* ... */ }
}
```

---

## 3. **YAGNI** – You Aren’t Gonna Need It

**Definition:**  
Don’t implement features until you actually need them.

**Example (Java):**
```java
// Don't add extra parameters or features "just in case"
void sendEmail(String to, String message) {
    // Only implement what's needed now
}
```

---

## 4. **SOC** – Separation of Concerns

**Definition:**  
Divide your code into distinct sections, each handling a specific responsibility.

**Example (Java):**
```java
class UserController {
    UserService service;
    void createUser(String name) { service.addUser(name); }
}

class UserService {
    void addUser(String name) { /* business logic */ }
}
```

---