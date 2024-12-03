### **Question 1: Java Program with Package, SpiderMan and SuperMan Classes**

#### i. **Creating the Package and Classes**:

```java
// File: SpiderMan.java (in americanSuperhero package)
package americanSuperhero;

public class SpiderMan {
    String movieName;
    String directedBy;

    // Constructor with 'this' reference
    public SpiderMan(String movieName, String directedBy) {
        this.movieName = movieName;
        this.directedBy = directedBy;
    }

    // Method to display movie information
    public void show() {
        System.out.println("Movie: " + movieName + ", Directed by: " + directedBy);
    }
}
```

```java
// File: SuperMan.java (in americanSuperhero package)
package americanSuperhero;

public class SuperMan {
    public static void main(String[] args) {
        // Create an object of SpiderMan class
        SpiderMan spiderMan = new SpiderMan("The Amazing Spider-Man 2", "Marc Webb");

        // Call the show() method of SpiderMan class
        spiderMan.show();
    }
}
```

#### **Expected Output**:

```
Movie: The Amazing Spider-Man 2, Directed by: Marc Webb
```

---

### **Question 2: Food Class and Subclasses Fastfood, Homemade**

#### i. **Creating the `Food`, `Fastfood`, and `Homemade` Classes**:

```java
// Food class
public class Food {
    Double calories, fat, carb;

    // Constructor
    Food(Double calories, Double fat, Double carb) {
        this.calories = calories;
        this.fat = fat;
        this.carb = carb;
    }

    // Method to print description
    void description() {
        System.out.println("Inside Food class");
    }
}
```

```java
// Fastfood class extending Food
public class Fastfood extends Food {
    // Constructor using super
    Fastfood(Double calories, Double fat, Double carb, Double calories2, Double fat2, Double carb2) {
        super(calories, fat, carb);
    }

    // Review method
    void Fastfoodreview() {
        System.out.println("Inside the review method of Fastfood class.");
    }
}
```

```java
// Homemade class extending Food
public class Homemade extends Food {
    // Constructor using super
    Homemade(Double calories, Double fat, Double carb, Double calories2, Double fat2, Double carb2) {
        super(calories, fat, carb);
    }

    // Review method
    void Homemadereview() {
        System.out.println("Inside the review method of Homemade class.");
    }

    // Overriding description method
    @Override
    void description() {
        System.out.println("Inside Homemade class");
    }
}
```

#### vi. **Using Subclass Polymorphism**:

```java
// Main class to test polymorphism
public class Foodmain {
    public static void main(String[] args) {
        Food f1 = new Homemade(100.0, 10.0, 20.0);
        Food f2 = new Fastfood(200.0, 15.0, 30.0);

        // Polymorphic call
        ((Homemade) f1).Homemadereview();
        ((Fastfood) f2).Fastfoodreview();
    }
}
```

#### **Expected Output**:

```
Inside the review method of Homemade class.
Inside the review method of Fastfood class.
```

---

### **Question 3: Code Output with Constructors and Blocks**

#### a. **Output of Code**:

```java
class Mid {
    int x = 10;
    
    {
        x = 20;
        System.out.println("@Block=" + x);
    }
    
    Mid(int x1, int x2) {
        x = x1 + x2;
        System.out.println("@Constructor-2=" + x);
    }
    
    Mid(int x1) {
        this(100, 200);
        x = x1;
        System.out.println("@Constructor-1=" + x);
    }
    
    Mid() {
        this(50);
        x = 30;
        System.out.println("@Constructor-0=" + x);
    }
}

public class InitBlock {
    public static void main(String[] args) {
        Mid obj1 = new Mid(30);
        System.out.println("@End=" + obj1.x);
    }
}
```

#### **Expected Output**:

```
@Block=20
@Constructor-2=300
@Constructor-1=30
@Constructor-0=30
@End=30
```

#### **Explanation**:

1. The instance block (`@Block=20`) runs first.
2. The constructors are called in the chain, printing each constructor’s value.

---

#### b. **Code Block with Point Class**:

```java
class Point {
    int x;
    int y;

    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
}

public class PointDemo {
    void resetPoint1(Point p) {
        p = new Point(0, 0);
    }

    void resetPoint2(Point p) {
        p.x = 0;
        p.y = 0;
    }

    public static void main(String[] args) {
        Point p1 = new Point(3, 5);
        Point p2 = new Point(10, 15);
        PointDemo demo = new PointDemo();
        demo.resetPoint1(p1);
        System.out.println("(" + p1.x + ", " + p1.y + ")");
        demo.resetPoint2(p2);
        System.out.println("(" + p2.x + ", " + p2.y + ")");
        p2 = new Point(9, 9);
    }
}
```

#### i. **Expected Output**:

```
(3, 5)
(0, 0)
```

#### ii. **Explanation of Garbage Collection**:

- When `p2 = new Point(9, 9)` is executed, the previous `Point(10, 15)` object is dereferenced and eligible for garbage collection if no other reference exists to it.

---

### **Question 4: Modify the Person Class and Test**

#### i. **Reason for Error and Modifying the Code**:

The error occurs because `id` and `name` are not accessible directly due to their access modifiers. To fix this, you can create getter methods in the `Person` class.

```java
class Person {
    private double id, height, weight;
    private String name;

    // Constructor (already written)
    public Person(double id, String name, double height, double weight) {
        this.id = id;
        this.name = name;
        this.height = height;
        this.weight = weight;
    }

    // Getter methods for id and name
    public double getId() {
        return id;
    }

    public String getName() {
        return name;
    }

    // BMI calculation method
    public double calculateBMI() {
        return weight / (height * height);
    }
}

public class Test {
    public static void main(String[] args) {
        Person p1 = new Person(1, "Steven", 1.75, 75);
        System.out.println("ID: " + p1.getId());
        System.out.println("Name: " + p1.getName());
    }
}
```

#### ii. **BMI Calculation**:

The `calculateBMI()` method is already included in the `Person` class. To access it:

```java
double bmi = p1.calculateBMI();
System.out.println("BMI: " + bmi);
```

#### iii. **Array of Person Objects**:

```java
Person[] persons = new Person[3];
persons[0] = new Person(1, "John", 1.8, 70);
persons[1] = new Person(2, "Mary", 1.65, 60);
persons[2] = new Person(3, "Steve", 1.75, 80);
```

---

### **Question 5: Code Output for Comics Class**

#### a. **Expected Output**:

```java
public class Comics {
    public void foo() {
        System.out.println("foo");
    }

    public void bar() {
        System.out.println("bar");
    }
}

public class Marvel extends Comics {
    public Marvel() {
        this(1000);
    }

    public Marvel(int val) {
        System.out.println("Value: " + val);
    }

    @Override
    public void foo() {
        super.foo();
        System.out.println("Tony Stark");
    }

    public void foo(double val) {
        System.out.println("Steve Rogers");
        System.out.println("Value: " + val);
    }

    public void fubar() {
        bar();
    }
}

public class Main {
    public static void main(String[] args) {
        Marvel obj = new Marvel();
        obj.foo();
        obj.foo(50);
        obj.fubar();
    }
}
```

#### **Expected Output**:

```
Value: 1000
foo
Tony Stark
Steve Rogers
Value: 50
bar
```

#### b. **Expected Output for Shape Class**:

```java
abstract class Shape {
    public abstract void printArea();
}

class Rectangle extends Shape {
    double width, height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    @Override
    public void printArea() {
        double area = width * height;
        System.out.println("Area: " + area);
    }
}

public class Main {
    public static void
```

main(String[] a) { Shape sh1, sh2; Rectangle r1 = new Rectangle(10, 20); sh1 = new Rectangle(10, 20); sh2 = new Rectangle(5, 10);

```
    r1.printArea();
    sh1.printArea();
    sh2.printArea();
}
```

}

```

#### **Expected Output**:
```

Area: 200 Area: 200 Area: 50


