# Core Java Interview Questions & Answers

<!-- TOC_START -->
| No. | Questions |
| --- | --------- |
<!-- TOC_END -->

## Questions

<!-- QUESTIONS_START -->

Question & Answer: Java Application Execution Flow
Q1: What are the key steps involved in creating a Java application?
A: Creating a Java application involves three main steps:

Writing Java Code – Write source code in a .java file using a text editor or an IDE.
Compiling the Code – Use the Java compiler (javac) to convert the .java file into bytecode (.class file).
Executing the Code – Run the compiled bytecode using the Java Virtual Machine (JVM).
Q2: How do you write Java code?
A: Java code is written in a .java file using a text editor (like Notepad++) or an IDE (such as IntelliJ IDEA, Eclipse, VS Code). It follows OOP principles (Encapsulation, Inheritance, Polymorphism, and Abstraction) and must comply with Java syntax rules.

Q3: What happens during the compilation process?
A: The Java compiler (javac) translates the .java file into a .class file containing bytecode. The compiler also checks for syntax errors—if any exist, the compilation fails until they are fixed.

Q4: What is bytecode and why is it important?
A: Bytecode is an intermediate, platform-independent code that allows Java programs to run on any operating system with a JVM. Unlike native machine code, bytecode requires interpretation or Just-In-Time (JIT) compilation at runtime.

Q5: How does the JVM execute Java programs?
A: The JVM (Java Virtual Machine) loads and interprets bytecode or compiles it Just-In-Time (JIT) for better performance. This allows Java applications to run seamlessly across different platforms like Windows, macOS, and Linux.

Q6: What is Java SE 11’s direct execution feature?
A: Java SE 11 introduced the ability to run single-file programs without explicit compilation. You can execute a .java file directly using:


java MyFile.java
This method skips generating a .class file but is only applicable for single-file programs.
Q7: Can you summarize the Java execution flow?
A: Sure! The Java program execution follows this sequence:

css
Copy
Edit
[Write Java Code] → [Compile (javac)] → [Generate Bytecode (.class)] → [Execute on JVM]
For Java 11+, you can directly run a .java file:

[Write Java Code] → [Direct Execution (java MyFile.java)]
This structured process ensures platform independence, error checking, and efficient execution of Java applications.
![Java Flowchart](imgs/javaCompilation.drawio.png)

## 1. What are the main features of Java?
### Answer:
Java is a high-level, object-oriented programming language with several key features:

- **Platform Independence:** Java follows the principle of "Write Once, Run Anywhere" (WORA) due to its JVM (Java Virtual Machine).
- **Object-Oriented:** Supports OOP concepts like encapsulation, inheritance, polymorphism, and abstraction.
- **Automatic Memory Management:** Java uses Garbage Collection (GC) to manage memory.
- **Multi-threading:** Java provides built-in support for concurrent programming.
- **Robust and Secure:** Java has strong type checking and security features such as bytecode verification and runtime security checks.
- **Rich API:** Java provides a vast standard library covering collections, networking, file handling, etc.
- **JIT Compiler:** Improves execution performance by converting bytecode to native machine code at runtime.

## 2. Explain the difference between JDK, JRE, and JVM.
### Answer:
- **JDK (Java Development Kit):** Includes JRE + development tools (compiler, debugger, etc.). Required for developing Java applications.
- **JRE (Java Runtime Environment):** Includes JVM + standard libraries. Needed to run Java applications but not to compile them.
- **JVM (Java Virtual Machine):** Converts bytecode into machine code for execution. It provides platform independence.

## 3. What are the principles of OOP in Java?
### Answer:
Java follows four key **Object-Oriented Programming (OOP)** principles:

1. **Encapsulation:** Data hiding using access modifiers (private, protected, etc.).
2. **Inheritance:** Allows a class to inherit properties from another class (extends keyword).
3. **Polymorphism:** Ability to perform different behaviors in different contexts (Method Overloading & Overriding).
4. **Abstraction:** Hiding implementation details and exposing only necessary functionalities (abstract classes & interfaces).

## 4. Explain the difference between `==` and `.equals()` in Java.
### Answer:
- `==` checks **reference equality** (whether two objects point to the same memory location).
- `.equals()` checks **content equality** (whether two objects contain the same data). 

Example:
```java
String s1 = new String("Hello");
String s2 = new String("Hello");
System.out.println(s1 == s2);       // false (Different memory locations)
System.out.println(s1.equals(s2));  // true (Same content)
```

## 5. What is the difference between `final`, `finally`, and `finalize()`?
### Answer:
- **`final`**: A keyword used to declare constants, prevent method overriding, or prevent class inheritance.
- **`finally`**: A block in exception handling that executes whether an exception is thrown or not.
- **`finalize()`**: A method called by the garbage collector before an object is removed from memory.

Example:
```java
final int MAX = 100; // Constant

try {
    int a = 5 / 0;
} catch (Exception e) {
    System.out.println("Exception caught");
} finally {
    System.out.println("Finally block executed");
}
```

## 6. What are Java access modifiers?
### Answer:
Java provides four access modifiers:

| Modifier  | Class | Package | Subclass | World |
|-----------|-------|---------|----------|--------|
| **public** | ✅ | ✅ | ✅ | ✅ |
| **protected** | ✅ | ✅ | ✅ | ❌ |
| **default (no modifier)** | ✅ | ✅ | ❌ | ❌ |
| **private** | ✅ | ❌ | ❌ | ❌ |

## 7. What are the different types of constructors in Java?
### Answer:
Java has three types of constructors:

1. **Default Constructor:** Provided by Java if no constructor is defined.
2. **Parameterized Constructor:** Accepts arguments to initialize an object.
3. **Copy Constructor:** Creates a copy of an existing object.

Example:
```java
class Car {
    String brand;
    
    // Default Constructor
    Car() {
        this.brand = "Toyota";
    }
    
    // Parameterized Constructor
    Car(String brand) {
        this.brand = brand;
    }
}
```

## 8. Explain the difference between `ArrayList` and `LinkedList`.
### Answer:
| Feature | ArrayList | LinkedList |
|---------|-----------|------------|
| Implementation | Uses a dynamic array | Uses a doubly linked list |
| Search Time | Fast (O(1) for index-based access) | Slow (O(n) for index-based access) |
| Insertion/Deletion | Slow (O(n) due to shifting) | Fast (O(1) if modifying head/tail) |
| Memory Overhead | Less | More (Extra memory for pointers) |

Use `ArrayList` when **searching is frequent**, and `LinkedList` when **frequent insertions/deletions occur**.

## 9. What is the Singleton Design Pattern?
### Answer:
Singleton ensures **only one instance** of a class exists.

### **Implementation in Java:**
```java
class Singleton {
    private static Singleton instance;
    
    private Singleton() {} // Private constructor
    
    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

## 10. What is the Factory Design Pattern?
### Answer:
Factory Pattern provides a way to instantiate objects without exposing logic.

### **Example:**
```java
interface Vehicle {
    void drive();
}
class Car implements Vehicle {
    public void drive() { System.out.println("Driving a Car"); }
}
class Bike implements Vehicle {
    public void drive() { System.out.println("Riding a Bike"); }
}
class VehicleFactory {
    public static Vehicle getVehicle(String type) {
        if (type.equals("Car")) return new Car();
        else if (type.equals("Bike")) return new Bike();
        return null;
    }
}
```
Usage:
```java
Vehicle vehicle = VehicleFactory.getVehicle("Car");
vehicle.drive();
```
### *What is Immutability?*

Immutability refers to the property of an object whose state cannot be modified after it is created. Once an immutable object is instantiated, its internal state (i.e., the values of its fields) remains constant throughout its lifetime. Any operation that appears to modify the object actually returns a new object with the updated state, leaving the original object unchanged.

### *Why is Immutability Important?*

1. *Thread Safety*: Immutable objects are inherently thread-safe because their state cannot change after creation. This eliminates the need for synchronization in multi-threaded environments.
2. *Predictability*: Since the state of an immutable object cannot change, it is easier to reason about and debug code.
3. *Caching and Reuse*: Immutable objects can be safely cached and reused, as their state will not change over time.
4. *Security*: Immutable objects are safer to use in sensitive contexts (e.g., as keys in a map) because their state cannot be altered.

---

### *1. Custom Immutable Class*

### *Steps to Create an Immutable Class*

1. *Make the class final*: Prevents subclassing, ensuring that no subclass can override methods and introduce mutability.
2. *Make all fields private and final*: Ensures that fields cannot be modified after initialization.
3. *Do not provide setter methods*: Prevents external modification of the object's state.
4. *Initialize all fields via constructor*: Ensures that fields are set only once during object creation.
5. *Perform defensive copying for mutable fields*: Prevents modification of nested mutable objects by creating copies of them.
6. *Prevent cloning*: Override the clone() method to throw an exception, preventing the creation of mutable copies.
7. *Ensure no mutable state is exposed*: Return copies of mutable fields to prevent external modification.

### *Example: Custom Immutable Class*

java
import java.util.ArrayList;
import java.util.List;

public final class ImmutablePerson {
    private final String name;
    private final int age;
    private final List<String> hobbies;

    // Constructor
    private ImmutablePerson(Builder builder) {
        this.name = builder.name;
        this.age = builder.age;
        this.hobbies = new ArrayList<>(builder.hobbies); // Defensive copy
    }

    // Getters
    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    public List<String> getHobbies() {
        return new ArrayList<>(hobbies); // Return a copy
    }

    @Override
    public String toString() {
        return "ImmutablePerson{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", hobbies=" + hobbies +
                '}';
    }

    // Builder class
    public static class Builder {
        private String name;
        private int age;
        private List<String> hobbies = new ArrayList<>();

        public Builder setName(String name) {
            this.name = name;
            return this;
        }

        public Builder setAge(int age) {
            this.age = age;
            return this;
        }

        public Builder addHobby(String hobby) {
            this.hobbies.add(hobby);
            return this;
        }

        public ImmutablePerson build() {
            return new ImmutablePerson(this);
        }
    }
}


---

### *Test Class for ImmutablePerson*

java
import java.util.List;

public class ImmutablePersonTest {
    public static void main(String[] args) {
        // Create an ImmutablePerson object using the builder
        ImmutablePerson person = new ImmutablePerson.Builder()
                .setName("John")
                .setAge(30)
                .addHobby("Reading")
                .addHobby("Swimming")
                .build();

        // Print the initial state of the object
        System.out.println("Initial Person: " + person);

        // Verify immutability by attempting to modify the object
        List<String> originalHobbies = new java.util.ArrayList<>();
        originalHobbies.add("Reading");
        originalHobbies.add("Swimming");

        ImmutablePerson person2 = new ImmutablePerson.Builder()
                .setName("Alice")
                .setAge(25)
                .addHobby("Dancing")
                .build();

        originalHobbies.add("Cooking");

        System.out.println("Original Hobbies List: " + originalHobbies);
        System.out.println("Person 2 Hobbies: " + person2.getHobbies());

        System.out.println("Person 1 (After Modification Attempt): " + person);
        System.out.println("Person 2 (After Modification Attempt): " + person2);

        List<String> personHobbies = person.getHobbies();
        personHobbies.add("Cooking");

        System.out.println("Person 1 Hobbies (After Modification Attempt): " + person.getHobbies());
        System.out.println("Person 1 (Final State): " + person);
    }
}


---

## *2. Predefined Immutable Classes in Java*

### *1. String*
- *Immutability*: Strings are immutable.
- *Internal Implementation: Uses a **String Constant Pool* to reuse strings.
- *Design Pattern: **Flyweight Pattern*.

java
String s1 = "Hello"; // Created in the pool
String s2 = "Hello"; // Reuses the same reference
System.out.println(s1 == s2); // true


---

### *2. Wrapper Classes (Integer, Long, Double, etc.)*
- *Immutability*: All wrapper classes are immutable.
- *Internal Implementation*: Caches frequently used values (e.g., -128 to 127 for Integer).
- *Design Pattern: **Flyweight Pattern*.

java
Integer a = 10; // Autoboxing (uses cached value)
Integer b = 10; // Reuses the cached value
System.out.println(a == b); // true


---

### *3. LocalDate, LocalTime, LocalDateTime (java.time package)*
- *Immutability*: All classes in the java.time package are immutable.
- *Internal Implementation*: Fields like year, month, and day are final.
- *Design Pattern: **Immutable Object Pattern*.

java
LocalDate date = LocalDate.of(2023, 10, 1);
LocalDate newDate = date.plusDays(5); // Returns a new instance
System.out.println(date); // 2023-10-01
System.out.println(newDate); // 2023-10-06


---

### *4. Collections.unmodifiableList(), unmodifiableSet(), etc.*
- *Immutability*: These methods return immutable views of collections.
- *Internal Implementation*: Throws UnsupportedOperationException for modification attempts.
- *Design Pattern: **Decorator Pattern*.

java
List<String> list = new ArrayList<>();
list.add("Java");
List<String> immutableList = Collections.unmodifiableList(list);
immutableList.add("Python"); // Throws UnsupportedOperationException


---

### *5. BigInteger and BigDecimal*
- *Immutability*: Both classes are immutable.
- *Internal Implementation*: Fields like int[] mag in BigInteger are final.
- *Design Pattern: **Immutable Object Pattern*.

java
BigInteger num1 = new BigInteger("100");
BigInteger num2 = num1.add(new BigInteger("200")); // Returns a new instance
System.out.println(num1); // 100
System.out.println(num2); // 300


---

## *3. Additional Scenarios*

### *1. Deep vs. Shallow Immutability*
- *Shallow Immutability*: Only the top-level object is immutable.
- *Deep Immutability*: The entire object graph is immutable.

java
final class ImmutablePerson {
    private final String name;
    private final List<Address> addresses;

    public ImmutablePerson(String name, List<Address> addresses) {
        this.name = name;
        this.addresses = new ArrayList<>(addresses); // Shallow copy
    }

    public List<Address> getAddresses() {
        return new ArrayList<>(addresses); // Shallow copy
    }
}


---

### *2. Serialization and Immutability*
- *Problem*: Serialization can break immutability.
- *Solution*: Override readObject() to prevent deserialization.

java
private void readObject(ObjectInputStream ois) throws IOException, ClassNotFoundException {
    throw new NotSerializableException("ImmutablePerson is not serializable");
}


---

### *3. Immutable Collections*
- Use List.of(), Set.of(), or Collections.unmodifiableList().

java
List<String> immutableList = List.of("Java", "Python", "C++");
immutableList.add("JavaScript"); // Throws UnsupportedOperationException


---

### *4. Immutable Classes with Optional Fields*
- Use the *Builder Pattern* for optional fields.

java
public static class Builder {
    private String email; // Optional field
    public Builder setEmail(String email) {
        this.email = email;
        return this;
    }
}


---

### *5. Immutable Classes with Lazy Initialization*
- Ensure thread safety for lazy-initialized fields.

java
private volatile List<String> hobbies; // Lazy initialized
public List<String> getHobbies() {
    if (hobbies == null) {
        synchronized (this) {
            if (hobbies == null) {
                hobbies = loadHobbiesFromDatabase();
            }
        }
    }
    return hobbies;
}


---

### *6. Immutable Classes with Validation*
- Validate input parameters during construction.

java
public ImmutablePerson(String name, int age) {
    if (name == null || name.trim().isEmpty()) {
        throw new IllegalArgumentException("Name cannot be null or empty");
    }
    this.name = name;
    this.age = age;
}


---

## *4. Design Patterns in Immutable Classes*

### *1. Flyweight Pattern*
- Used in String and wrapper classes to reuse shared objects.

### *2. Immutable Object Pattern*
- Used in LocalDate, BigInteger, and BigDecimal.

### *3. Decorator Pattern*
- Used in Collections.unmodifiableList().

---

## *5. Key Takeaways*
1. *Immutability* ensures thread safety, predictability, and caching.
2. *Defensive copying* is crucial for mutable fields.
3. *Predefined immutable classes* like String, Integer, and LocalDate follow design patterns like Flyweight and Immutable Object.
4. *Additional scenarios* include deep vs. shallow immutability, serialization, lazy initialization, and validation.
<!-- QUESTIONS_END -->



