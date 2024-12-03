Let’s dive into a **comprehensive and dedicated lecture** covering the following key topics in Object-Oriented Programming (OOP):

1. **Class and Object Basics**
2. **Inheritance**
3. **Encapsulation**
4. **Polymorphism**
5. **Abstract Classes**
6. **Static Context**

---

### **1. Class and Object Basics**

#### **1.1 What is a Class?**

- A **class** is a blueprint or template for creating objects (instances).
- It defines the **properties** (attributes) and **behaviors** (methods) that objects created from the class will have.

##### **Syntax of a Class:**

```java
public class Car {
    // Instance variables (attributes)
    String model;
    String brand;
    int year;

    // Constructor (initializes the object)
    public Car(String model, String brand, int year) {
        this.model = model;
        this.brand = brand;
        this.year = year;
    }

    // Method (behavior)
    public void displayInfo() {
        System.out.println("Model: " + model + ", Brand: " + brand + ", Year: " + year);
    }
}
```

#### **1.2 What is an Object?**

- An **object** is an instance of a class. It has its own unique set of values for the class's attributes and can call the class's methods.

##### **Creating an Object:**

```java
public class Main {
    public static void main(String[] args) {
        // Creating an object (instance) of the class
        Car myCar = new Car("Model S", "Tesla", 2022);
        
        // Calling a method of the object
        myCar.displayInfo();  // Output: Model: Model S, Brand: Tesla, Year: 2022
    }
}
```

#### **1.3 Constructors:**

- A **constructor** is a special method used to initialize objects.
- There are **two types of constructors**:
    - **Default constructor** (no parameters).
    - **Parameterized constructor** (with parameters to initialize attributes).

##### **Default Constructor:**

```java
public class Car {
    String brand;
    String model;

    // Default constructor
    public Car() {
        this.brand = "Unknown";
        this.model = "Unknown";
    }
}
```

##### **Parameterized Constructor:**

```java
public class Car {
    String brand;
    String model;

    // Parameterized constructor
    public Car(String brand, String model) {
        this.brand = brand;
        this.model = model;
    }
}
```

#### **1.4 Static Blocks, Static Variables, and Static Methods**

- **Static variables** are shared across all instances of the class.
- **Static methods** can be called without creating an object.
- **Static blocks** run once when the class is loaded into memory.

##### **Static Example:**

```java
public class Car {
    static int count = 0;  // Static variable
    
    // Static block
    static {
        System.out.println("Car class loaded.");
        count++;
    }

    // Constructor
    public Car() {
        count++;
    }

    // Static method
    public static void displayCount() {
        System.out.println("Number of cars: " + count);
    }
}
```

---

### **2. Inheritance**

#### **2.1 What is Inheritance?**

- **Inheritance** is a mechanism where a new class (child class) inherits attributes and methods from an existing class (parent class).
- It promotes **code reusability** and establishes a relationship between different classes.

##### **Syntax of Inheritance:**

```java
// Parent class
public class Animal {
    String name;

    public void speak() {
        System.out.println("Animal is speaking.");
    }
}

// Child class inheriting from Animal
public class Dog extends Animal {
    public void speak() {
        System.out.println("Dog is barking.");
    }
}
```

#### **2.2 Using `super()` to Call Parent Class Constructors and Methods**

- The `super()` keyword is used to call the parent class's constructor or method.

##### **Example:**

```java
// Parent class
public class Animal {
    String name;

    public Animal(String name) {
        this.name = name;
    }

    public void speak() {
        System.out.println(name + " is speaking.");
    }
}

// Child class
public class Dog extends Animal {
    public Dog(String name) {
        super(name);  // Calling parent class constructor
    }

    @Override
    public void speak() {
        super.speak();  // Calling parent class method
        System.out.println("Dog is barking.");
    }
}
```

#### **2.3 Overriding Methods in Child Classes**

- **Method overriding** allows a child class to provide a specific implementation of a method that is already defined in the parent class.

##### **Example:**

```java
// Parent class
public class Animal {
    public void speak() {
        System.out.println("Animal is speaking.");
    }
}

// Child class
public class Dog extends Animal {
    @Override
    public void speak() {
        System.out.println("Dog is barking.");
    }
}
```

---

### **3. Encapsulation**

#### **3.1 Access Modifiers:**

- **Private**: Accessible only within the class.
- **Protected**: Accessible within the same package and by subclasses.
- **Public**: Accessible from anywhere.

#### **3.2 Getters and Setters:**

- **Getter** methods provide access to private variables.
- **Setter** methods allow you to modify private variables.

##### **Example:**

```java
public class Person {
    private String name;  // Private variable

    // Getter
    public String getName() {
        return name;
    }

    // Setter
    public void setName(String name) {
        this.name = name;
    }
}
```

---

### **4. Polymorphism**

#### **4.1 Method Overloading:**

- **Method overloading** allows multiple methods with the same name but different parameter lists.

##### **Example:**

```java
public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }

    public double add(double a, double b) {
        return a + b;
    }
}
```

#### **4.2 Method Overriding:**

- **Method overriding** is when a subclass provides its own implementation of a method that is already defined in the parent class.

##### **Example:**

```java
// Parent class
public class Animal {
    public void sound() {
        System.out.println("Animal sound");
    }
}

// Child class
public class Dog extends Animal {
    @Override
    public void sound() {
        System.out.println("Bark");
    }
}
```

#### **4.3 Subclass Polymorphism:**

- You can refer to a child class object using a parent class reference.

##### **Example:**

```java
public class Main {
    public static void main(String[] args) {
        Animal animal = new Dog();  // Parent class reference to child class object
        animal.sound();  // Output: Bark
    }
}
```

---

### **5. Abstract Classes**

#### **5.1 Declaring Abstract Methods and Classes:**

- An **abstract class** cannot be instantiated directly.
- An **abstract method** has no implementation in the parent class and must be implemented by subclasses.

##### **Example:**

```java
// Abstract class
public abstract class Shape {
    public abstract void draw();
}

// Concrete class
public class Circle extends Shape {
    @Override
    public void draw() {
        System.out.println("Drawing a circle");
    }
}
```

#### **5.2 Implementing Abstract Methods:**

- Subclasses that extend an abstract class **must** provide an implementation for all abstract methods.

##### **Example:**

```java
public abstract class Animal {
    public abstract void sound();
}

public class Cat extends Animal {
    @Override
    public void sound() {
        System.out.println("Meow");
    }
}
```

---

### **6. Static Context**

#### **6.1 Static Variables and Methods:**

- **Static variables** are shared across all instances of a class.
- **Static methods** can be called without creating an instance of the class.

##### **Example:**

```java
public class Counter {
    static int count = 0;  // Static variable

    public static void increment() {
        count++;
    }

    public static void displayCount() {
        System.out.println("Count: " + count);
    }
}
```

#### **6.2 Static Blocks:**

- A **static block** is executed when the class is loaded into memory. It's used for initialization.

##### **Example:**

```java
public class StaticExample {
    static {
        System.out.println("Class Loaded");
    }

    public static void main(String[] args) {
        System.out.println("Main method executed");
    }
}
```

#### **6.3 Static and Instance Blocks:**

- **Instance blocks** are executed when an object is created, and **static blocks** are executed when the class is loaded.

---

