
---

### **Question 1: Expected Output of `SomeClass`**

#### Code:

```java
public class SomeClass {
    SomeClass(){
        System.out.println("I am the base constructor");
    }

    SomeClass(int a){
        this(); // Calls the no-argument constructor
        System.out.println("I have an extra value: " + a);
        this.someMethod(a); // Calls the overloaded method with int parameter
    }

    SomeClass(int a, double b){
        this(a); // Calls the constructor with one int parameter
        System.out.println("I have more values: " + b);
    }

    public void someMethod(){
        System.out.println("I have no param");
    }

    public void someMethod(int c){
        System.out.println("I borrow " + c + " from a constructor");
    }
}

public class Main {
    public static void main(String[] args) {
        SomeClass s = new SomeClass(5, 6.3); // Calls the constructor with two parameters
        s.someMethod(); // Calls the no-parameter method
    }
}
```

#### **Expected Output:**

```
I am the base constructor
I have an extra value: 5
I have more values: 6.3
I have no param
```

#### **Explanation:**

- The constructor chain works as follows:
    - `SomeClass(5, 6.3)` calls the constructor `SomeClass(int a, double b)`, which in turn calls `SomeClass(int a)`, which calls the no-argument constructor.
    - After that, it prints `"I have an extra value: 5"` and `"I have more values: 6.3"`.
- Then, `someMethod()` with no parameters is called, printing `"I have no param"`.

---

### **Question 2: Classes `Human`, `Monster`, and `Test`**

#### (a) **Correct the code by adding necessary getter methods:**

```java
package M1;
public class Human {
    private int id;
    String intelligence;
    protected boolean bravery;

    // Constructor
    public Human(int id, String intelligence, boolean bravery) {
        this.id = id;
        this.intelligence = intelligence;
        this.bravery = bravery;
    }

    // Getter for id (readonly)
    public int getId() {
        return id;
    }

    // Getter for intelligence (readonly)
    public String getIntelligence() {
        return intelligence;
    }

    // Getter for bravery (readonly)
    public boolean isBravery() {
        return bravery;
    }
}

public class Monster {
    String name;
    double weight;

    public Monster(String name, double weight) {
        this.name = name;
        this.weight = weight;
    }

    public void increaseWeight(double weight) {
        System.out.println("New weight of monster=" + (this.weight + weight));
    }

    boolean eat(Human h) {
        return h.getIntelligence().equals("high");
    }

    String scare(boolean bravery) {
        if (!bravery) {
            return "Human scared.";
        } else {
            return "Human is too brave to scare.";
        }
    }
}
```

#### (b) **Write necessary constructors and blocks for output:**

```java
package M1.M2;

public class Test {
    public static void main(String[] args) {
        Human h1 = new Human(1, "low", true);
        Human h2 = new Human(2, "high", false);
        Monster m1 = new Monster("CookieMonster", 100);
        
        if (m1.eat(h1) == true) {
            System.out.println("Monster has eaten human " + h1.getId());
        } else {
            System.out.println("Human escaped");
        }
        System.out.println(m1.scare(h2.isBravery()));
    }
}
```

#### **Expected Output:**

```
Monster has eaten human 1
Human is too brave to scare.
New weight of monster=110.0
```

#### **Explanation:**

- The `eat()` method checks the intelligence of a `Human` object. If it's "high", the monster eats the human; otherwise, it increases its weight and returns `false`.
- The `scare()` method checks bravery and prints the appropriate message.
- Constructor and getter methods are necessary for encapsulating the `Human` class data.

---

### **Question 3: Implementing `AdvancedCalculator` Class**

#### Code for `Calculator` and `AdvancedCalculator`:

```java
public class Calculator {
    public int a;
    public int b;

    Calculator(int firstNumber, int secondNumber) {
        this.a = firstNumber;
        this.b = secondNumber;
    }

    public int sum() {
        return a + b;
    }

    public int subtract() {
        return a - b;
    }
}

public class AdvancedCalculator extends Calculator {
    private int[] numbers;

    // Constructor that initializes the 'numbers' array
    AdvancedCalculator(int firstNumber, int secondNumber, int[] numbers) {
        super(firstNumber, secondNumber);
        this.numbers = numbers;
    }

    // Overriding the sum method
    @Override
    public int sum() {
        int sum = super.sum();  // Summing first two numbers using parent class method
        for (int num : numbers) {
            sum += num;  // Adding additional numbers
        }
        return sum;
    }

    // Main class
    public static void main(String[] args) {
        AdvancedCalculator c = new AdvancedCalculator(1, 2, new int[]{3, 4, 5});
        System.out.println("Subtraction result: " + c.subtract());  // Should print: -1
        System.out.println("Summation result: " + c.sum());  // Should print: 15
    }
}
```

#### **Expected Output:**

```
Subtraction result: -1
Summation result: 15
```

#### **Explanation:**

- The `AdvancedCalculator` extends `Calculator`. The constructor of `AdvancedCalculator` initializes the `numbers` array.
- The `sum()` method is overridden to use the `sum()` method from the parent `Calculator` class and then adds the elements of `numbers[]`.

---

### **Question 4: Parent and Child Classes with Static Methods**

#### Code:

```java
public class Parent {
    public static int count = 0;

    public static void printDetails() {
        count++;
        System.out.println("I am in Parent Class: " + count);
    }
}

public class Child extends Parent {
    public static void printDetails() {
        count++;
        System.out.println("I am in a Child Class: " + count);
    }
}

public class Main {
    public static void main(String[] args) {
        Child x = new Child();
        x.printDetails();  // Calls Child's printDetails
        x.printDetails();  // Calls Child's printDetails

        Parent y = new Parent();
        y.printDetails();  // Calls Parent's printDetails
        Child.printDetails();  // Calls Child's printDetails
        Parent.printDetails();  // Calls Parent's printDetails
        x.printDetails();  // Calls Child's printDetails
    }
}
```

#### **Expected Output:**

```
I am in a Child Class: 1
I am in a Child Class: 2
I am in Parent Class: 3
I am in a Child Class: 4
I am in Parent Class: 5
I am in a Child Class: 6
```

#### **Explanation:**

- Static methods and variables are shared across all instances of a class.
- The `count` variable is shared between the `Parent` and `Child` classes, so each call to `printDetails()` increments it.

---

### **Question 5: Errors in Code and Explanation**

#### Code Errors:

```java
class Point {
    int x, y;
    final int f = 10;
    final Point p = new Point(1, 2);

    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
}

class Check {
    public static void main(String args[]) {
        Point point = new Point(5, 5);
        point.f = 5;  // Error: f is a final variable, cannot be reassigned
        point.p.x = 10;  // Error: Cannot modify p.x because p is final
        point.p = new Point(1, 5);  // Error: Cannot reassign p because it is final
    }
}
```

#### **Explanation:**

- `f` is a `final` variable, so it cannot be modified after initialization.
- `p` is also a `final` reference, so it cannot be reassigned after it's initialized, and its members cannot be modified.

---

### **Question 6: Cake Class and Derived Classes**

#### Code for `OrderCake` and `ReadymadeCake`:

```java
public class Cake {
    protected String name;
    protected double rate;

    public Cake(String n, double r) {
        name = n;
        rate = r;
    }

    public double calcPrice() {
        System.out.println("Print the calculated price.");
        return 0.0;  // Default behavior
    }

    public void printDetails() {
        System.out.println("Prints the detail.");
    }
}

class OrderCake extends Cake {
    double weight;

    public OrderCake(String n, double r, double w) {
        super(n, r);
        weight = w;
    }

    @Override
    public double calc
```

Price() { return rate * weight; }

```
@Override
public void printDetails() {
    System.out.println("Name: " + name);
    System.out.println("Rate: " + rate);
    System.out.println("Weight: " + weight);
    System.out.println("Total Price: " + calcPrice());
}
```

}

class ReadymadeCake extends Cake { int quantity;

```
public ReadymadeCake(String n, double r, int q) {
    super(n, r);
    quantity = q;
}

@Override
public double calcPrice() {
    return rate * quantity;
}

@Override
public void printDetails() {
    System.out.println("Name: " + name);
    System.out.println("Rate: " + rate);
    System.out.println("Quantity: " + quantity);
    System.out.println("Total Price: " + calcPrice());
}
```

}

class Main { public static void main(String[] args) { Cake[] cake = new Cake[3]; cake[0] = new OrderCake("OrderCake", 150, 3); cake[1] = new OrderCake("OrderCake", 200, 4); cake[2] = new ReadymadeCake("ReadymadeCake", 200, 2);

```
    for (Cake c : cake) {
        c.printDetails();
    }
}
```

}

```

#### **Expected Output:**
```

Name: OrderCake Rate: 150.0 Weight: 3.0 Total Price: 450.0 Name: OrderCake Rate: 200.0 Weight: 4.0 Total Price: 800.0 Name: ReadymadeCake Rate: 200.0 Quantity: 2 Total Price: 400.0

```

#### **Explanation:**
- The `OrderCake` and `ReadymadeCake` classes override `calcPrice()` and `printDetails()` to provide specific implementations for calculating price and printing details.

---