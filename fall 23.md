
### Q1: **Logarithm Class and Myfunc Method**

#### (a) **Logarithm Class Implementation:**

You need to write a class `Logarithm` with the given structure and logic to compute logarithms based on the formula:

log⁡bx=log⁡exlog⁡eb\log_b x = \frac{\log_e x}{\log_e b}

Where `log_e` can be evaluated by `Math.log(x)` in Java.

#### **Code:**

```java
public class Logarithm {
    int b;
    double x;

    // Constructor with base and argument
    public Logarithm(int b, double x) {
        this.b = b;
        this.x = x;
    }

    // Copy constructor
    public Logarithm(Logarithm log) {
        this.b = log.b;
        this.x = log.x;
    }

    // Default constructor
    public Logarithm() {
        this.b = 0;
        this.x = 0.0;
    }

    // Method to calculate logarithm
    public double myfunc() {
        return Math.log(x) / Math.log(b);  // log_b(x) = log(x) / log(b)
    }
}

public class Main {
    public static void main(String[] args) {
        Logarithm log1 = new Logarithm(2, 9);  // base=2, argument=9
        Logarithm log2 = new Logarithm(log1);  // copy constructor
        Logarithm log3 = new Logarithm();  // default constructor
        System.out.println(log1.b + " " + log1.x + " " + log1.myfunc());
        System.out.println(log2.b + " " + log2.x + " " + log2.myfunc());
        System.out.println(log3.b + " " + log3.x + " " + log3.myfunc());
    }
}
```

#### **Expected Output:**

```
2 9.0 3.0
2 9.0 3.0
0 0.0 0.0
```

#### Explanation:

- `log1` has base `2` and argument `9`, so `log_2(9)` is calculated.
- `log2` is a copy of `log1`, so the values of `b` and `x` are the same.
- `log3` is initialized with default values (base `0` and argument `0`), so `log_0(0)` results in `0.0`.

---

#### (b) **Animal and Pokemon Classes Output:**

```java
public class Animal {
    public String color;
    public String name;

    public Animal() {
        System.out.println("Default animal");
        color = "Unknown";
    }

    public void showNameColor() {
        System.out.println("Color is: " + color + " Name is: " + name);
    }

    {
        System.out.println("Animal instance initialization ");
    }
}

public class Pokemon extends Animal {
    public String name = "Pikachu";
    public String color = "Red";
}

public class AnimalTest {
    public static void main(String[] args) {
        Animal defaultAnimal = new Animal();
        Animal pk = new Pokemon();
        defaultAnimal.showNameColor();
        pk.showNameColor();
    }
}
```

#### **Expected Output:**

```
Animal instance initialization 
Default animal
Color is: Unknown Name is: null
Color is: Red Name is: Pikachu
```

#### Explanation:

- **Instance Initialization Block**: Prints `"Animal instance initialization "` before the constructor runs.
- **Pokemon Object**: The `Pokemon` class overrides the `color` and `name` fields, but since the `showNameColor()` method in `Pokemon` uses the inherited `name` and `color` fields, it prints `Pikachu` and `Red`.

---

### Q2: **BankAccount Class with Getter/Setter Methods**

#### (a) **Correcting BankAccount Class with Getters/Setters:**

```java
public class BankAccount {
    public String name;
    private String account_id;
    private double balance;

    BankAccount(String name, double balance, String gender) {
        this.name = name;
        this.balance = balance;
        this.account_id = gender + "-" + name;
    }

    // Getter for account_id
    public String getAccountId() {
        return account_id;
    }

    // Getter and Setter for balance
    public double getBalance() {
        return balance;
    }

    public void setBalance(double balance) {
        if (balance >= 0) {
            this.balance = balance;
        } else {
            System.out.println("Balance cannot be less than 0");
        }
    }
}

class Test {
    public static void main(String[] args) {
        BankAccount b = new BankAccount("Mr.Rahman", 1000, "M");
        System.out.println("Account id: " + b.getAccountId());
        System.out.println("Balance before: " + b.getBalance());
        b.setBalance(b.getBalance() - 2000);  // This will trigger balance cannot be less than 0
    }
}
```

#### **Explanation:**

- Added getter and setter methods for `balance` and `account_id`.
- Ensured that `balance` cannot be set to a negative value using `setBalance()`.

---

#### (b) **PizzaShop Class with Order Methods:**

```java
public class PizzaShop {
    private int pizza_price = 320;
    private int drink_price = 40;
    private int fries_price = 100;

    // Constructor
    PizzaShop() {
        System.out.println("Welcome to pizza shop");
    }

    // Method to order pizzas, drinks, and fries
    public void order(int pizzas, int drinks) {
        int total = pizzas * pizza_price + drinks * drink_price;
        System.out.println("You ordered " + pizzas + " pizzas, " + drinks + " drinks");
        System.out.println("Total bill: " + total + " taka");
    }

    // Overloaded method to order pizzas, drinks, and fries
    public void order(int pizzas, int drinks, int fries) {
        int total = pizzas * pizza_price + drinks * drink_price + fries * fries_price;
        System.out.println("You ordered " + pizzas + " pizzas, " + drinks + " drinks, " + fries + " fries");
        System.out.println("Total bill: " + total + " taka");
    }

    // Overloaded method to order only pizzas
    public void order(int pizzas) {
        int total = pizzas * pizza_price;
        System.out.println("You ordered " + pizzas + " pizzas");
        System.out.println("Total bill: " + total + " taka");
    }
}

class Order {
    public static void main(String[] args) {
        PizzaShop p = new PizzaShop();
        p.order(2, 4);
        p.order(1, 2, 1);
        p.order(3);
    }
}
```

#### **Expected Output:**

```
Welcome to pizza shop
You ordered 2 pizzas, 4 drinks
Total bill: 800 taka
You ordered 1 pizzas, 2 drinks, 1 fries
Total bill: 500 taka
You ordered 3 pizzas
Total bill: 960 taka
```

#### Explanation:

- The `PizzaShop` class has three overloaded `order()` methods to handle different combinations of ordered items.

---

### Q3: **Vehicle and Car Classes**

#### **Car Class Implementation:**

```java
public class Vehicle {
    private String make;
    private String model;

    public Vehicle(String make, String model) {
        this.make = make;
        this.model = model;
    }

    public void start() {
        System.out.println("[Vehicle] The vehicle is starting.");
    }

    public void stop() {
        System.out.println("[Vehicle] The vehicle is stopping.");
    }

    public void drive() {
        System.out.println("[Vehicle] The vehicle is moving.");
    }
}

public class Car extends Vehicle {
    private int numberOfDoors;

    public Car(String make, String model, int numberOfDoors) {
        super(make, model);
        this.numberOfDoors = numberOfDoors;
    }

    @Override
    public void drive() {
        super.drive();
        System.out.println("[Car] The car is moving.");
    }

    public void honk() {
        System.out.println("[Car] Honk! Honk!");
    }
}

public class Main {
    public static void main(String[] args) {
        Vehicle car1 = new Car("make001", "model001", 4);
        car1.drive();
        // car1.honk(); // This will cause an error because 'honk()' is not in Vehicle class.
    }
}
```

#### **Explanation:**

- **Car Class**: The `Car` class extends `Vehicle`, overrides `drive()`, and adds a `honk()` method.
- **Output**: The `car1.drive()` prints messages from both `Vehicle` and `Car`. However, the `honk()` method cannot be called on `Vehicle` since it is not available in the `Vehicle` class.

#### Expected Output:

```
[Vehicle] The vehicle is moving.
[Car] The car is moving.
```

---

### Q4: **Ride Class with Speed Limit and Penalty Calculations**

#### (a) **Ride Class Implementation:**

```java
public abstract class Ride {
    static final int speedLimit = 80;  // static and final

    public abstract double getHighestAccelerationTime();
    public abstract double calculateFine(int hour);
}

```

class Bike extends Ride { int initial_speed = 20; int acceleration = 2;

```
@Override
public double getHighestAccelerationTime() {
    return (speedLimit - initial_speed) / (double) acceleration;
}

@Override
public double calculateFine(int hour) {
    double fine = 50 + (hour - 1) * 100;  // Base fine and extra for exceeding speed limit
    return fine;
}
```

}

class Car extends Ride { int initial_speed = 40; int acceleration = 10;

```
@Override
public double getHighestAccelerationTime() {
    return (speedLimit - initial_speed) / (double) acceleration;
}

@Override
public double calculateFine(int hour) {
    double fine = 100 + (hour - 1) * 150;
    return fine;
}
```

}

class Microbus extends Ride { int initial_speed = 15; int acceleration = 5;

```
@Override
public double getHighestAccelerationTime() {
    return (speedLimit - initial_speed) / (double) acceleration;
}

@Override
public double calculateFine(int hour) {
    return 3000;  // Fixed fine for exceeding speed limit
}
```

}

````

#### (b) **Calculating Fine and Acceleration Time**

- Use the formula \( v = u + at \) to find time needed to reach the speed limit for each vehicle.
- **Fine** is calculated based on the number of hours exceeding the speed limit.

---

### Q5: **Abstract Class and Abstract Methods**

#### (a) **Can you define an abstract method in a non-abstract class?**

No, abstract methods can only be defined in **abstract classes**. If you define an abstract method in a non-abstract class, it will cause a compilation error.

#### (b) **Can abstract classes contain variables?**

Yes, abstract classes can contain variables. An abstract class can have **fields** (variables) and can also have **abstract methods** that subclasses must implement.

#### (c) **Abstract Class `ReadingMaterial` and Subclasses `Book` and `Magazine`:**

```java
abstract class ReadingMaterial {
    private String title;
    private String author;
    private int year;

    public ReadingMaterial(String title, String author, int year) {
        this.title = title;
        this.author = author;
        this.year = year;
    }

    abstract void displayDetails();
}

class Book extends ReadingMaterial {
    private String genre;

    public Book(String title, String author, int year, String genre) {
        super(title, author, year);
        this.genre = genre;
    }

    @Override
    void displayDetails() {
        System.out.println("Book: " + title + " by " + author + ", Year: " + year + ", Genre: " + genre);
    }
}

class Magazine extends ReadingMaterial {
    private int issueNumber;

    public Magazine(String title, String author, int year, int issueNumber) {
        super(title, author, year);
        this.issueNumber = issueNumber;
    }

    @Override
    void displayDetails() {
        System.out.println("Magazine: " + title + " by " + author + ", Year: " + year + ", Issue No: " + issueNumber);
    }
}
````

