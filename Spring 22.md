
---

### **Question 1: Marks Class**

#### (a) **Create a class named `Marks` with four instance variables:**

```java
public class Marks {
    String id;
    double quizMark;
    double midMark;
    double finalMark;
    
    // Constructor to initialize the instance variables
    public Marks(String id, double quizMark, double midMark, double finalMark) {
        this.id = id;
        this.quizMark = quizMark;
        this.midMark = midMark;
        this.finalMark = finalMark;
    }

    // Method to calculate total mark and check pass/fail
    public void passedOrNot() {
        double totalMark = quizMark + midMark + finalMark;
        if (totalMark >= 55) {
            System.out.println("passed");
        } else {
            System.out.println("failed");
        }
    }

    public static void main(String[] args) {
        // Create Marks objects
        Marks student1 = new Marks("S123", 20, 15, 30);
        Marks student2 = new Marks("S456", 30, 20, 10);
        
        // Call passedOrNot method for each student
        student1.passedOrNot();
        student2.passedOrNot();
    }
}
```

#### **Explanation:**

- The `Marks` class has four instance variables: `id`, `quizMark`, `midMark`, and `finalMark`.
- A parameterized constructor initializes these variables.
- The `passedOrNot()` method calculates the total marks and prints "passed" if the total is greater than or equal to 55, otherwise it prints "failed".

#### **Expected Output:**

```
passed
failed
```

---

### **Question 2: Code Completion**

Let's break this into its respective parts:

#### (a) **Public getter/setter methods for variable `b`:**

```java
public class SuperClass {
    private int b;

    // Getter method for b
    public int getB() {
        return b;
    }

    // Setter method for b
    public void setB(int b) {
        this.b = b;
    }
}
```

#### (b) **Constructor with three parameters:**

```java
public class SubClass extends SuperClass {
    private int c;

    // Constructor with three parameters
    public SubClass(int a, int b, int c) {
        super();  // Call the constructor of the superclass
        this.c = c;
        setB(b);   // Using setter method to initialize b
    }

    @Override
    public void show() {
        System.out.println(a + b + c); // Summation of a, b, and c
    }
}
```

#### (c) **Constructor with object passed as a parameter:**

```java
public SubClass(SubClass other) {
    super();
    this.c = other.c;
    setB(other.getB());
}
```

#### (d) **Overriding `show()` method:**

```java
@Override
public void show() {
    System.out.println(a + b); // Summation of a and b
}
```

#### **Explanation:**

- A getter and setter method for variable `b` is provided to allow access from outside the class.
- A constructor is added that accepts three parameters and initializes the superclass using `super()`.
- The `show()` method is overridden to print the sum of the variables `a`, `b`, and `c` for the first case, and only `a` and `b` for the second case.

---

### **Question 3: Code Output**

#### (a) **Write the output of the following code:**

```java
public class Book {
    public void show() {
        System.out.println("Books are awesome!");
    }
}

public class Paperback extends Book {
    public void show() {
        super.show(); // Call the parent class method
        System.out.println("Paperback books are good for your eyes!");
    }
}

public class Marker extends Paperback {
    public void show() {
        super.show(); // Call the parent class method
        System.out.println("Page marker was put on page no: 50");
    }
}

public class Main {
    public static void main(String[] args) {
        Book book = new Marker(); // Marker class object
        book.show();  // Calls overridden show() method in Marker class
    }
}
```

#### **Expected Output:**

```
Books are awesome!
Paperback books are good for your eyes!
Page marker was put on page no: 50
```

#### **Explanation:**

- The `Marker` class overrides the `show()` method of `Paperback`, which itself calls the `show()` method of `Book`. Therefore, the `show()` method in `Marker` prints all the messages in sequence.

#### (b) **Fix the errors and produce the correct output:**

```java
// In the class Marker, add the following lines:
public void show() {
    super.show();  // Call the method in the Paperback class
    System.out.println("Page marker was put on page no: 50");
}
```

---

### **Question 4: GeometricShape, Sphere, and Cylinder Classes**

#### (a) **Sphere Class Inheriting GeometricShape:**

```java
public class GeometricShape {
    public double volume() {
        return 0.0; // Default volume for a general shape
    }
}

public class Sphere extends GeometricShape {
    private double radius;

    public Sphere(double radius) {
        this.radius = radius;
    }

    @Override
    public double volume() {
        return (4.0 / 3.0) * Math.PI * Math.pow(radius, 3);  // Volume formula for sphere
    }
}
```

#### (b) **Cylinder Class Inheriting GeometricShape:**

```java
public class Cylinder extends GeometricShape {
    private double radius;
    private double height;

    public Cylinder(double radius, double height) {
        this.radius = radius;
        this.height = height;
    }

    @Override
    public double volume() {
        return Math.PI * Math.pow(radius, 2) * height;  // Volume formula for cylinder
    }
}
```

#### **Explanation:**

- The `Sphere` class calculates the volume of a sphere using the formula 43πr3\frac{4}{3} \pi r^3.
- The `Cylinder` class calculates the volume of a cylinder using the formula πr2h\pi r^2 h.

---

### **Question 5: Access Control and Garbage Collection**

#### (a) **Creating an object of class `A` from `pack1` in class `B`:**

```java
// In class B:
A a = new A();  // Create an object of class A from pack1
```

#### (b) **Correct Access Specifier for Variable `x` in A:**

```java
public class A {
    public int x;  // Set the access specifier of x to public
}
```

#### (ii) **Values printed in Line 31 and 33:**

In order to determine the values printed, the context of the code is missing. Typically, the line numbers correspond to statements in the main method, where objects are printed or methods are called. If you can provide more context, I can help with the exact values.

#### (iii) **Mark objects for Garbage Collection:**

Objects are marked for garbage collection when there are no references to them. If you update or nullify references to objects, they can be collected by the garbage collector.

Example:

```java
A a = new A();  // Object a created
a = null;        // Now a is eligible for garbage collection
```

---

