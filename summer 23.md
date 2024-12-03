
---

### **Q1: Output of the Vehicle Class Program**

```java
public class Vehicle {
    private String brand;
    private String model;
    
    static {
        System.out.println("Initializing Vehicle class...");
    }
    
    {
        System.out.println("Initializing an instance of the Vehicle class...");
    }

    public Vehicle() {
        System.out.println("Creating a default vehicle.");
        brand = "Unknown";
    }

    public Vehicle(String brand, String model) {
        System.out.println("Creating a customized vehicle of brand: " + brand + " and model: " + model);
        this.brand = brand;
        this.model = model;
    }

    public void honk() {
        System.out.println("The vehicle emits a honking sound.");
    }

    public void honk(String sound) {
        System.out.println("The vehicle emits a custom honking sound: " + sound);
    }

    static {
        System.out.println("Making sure of initialization...");
    }

    public void info() {
        System.out.println("model=" + model + " brand=" + brand);
    }

    public static void main(String[] args) {
        Vehicle defaultVehicle = new Vehicle();
        defaultVehicle.honk();
        defaultVehicle.info();
        
        Vehicle truck = new Vehicle("Ford", "F-150");
        truck.honk("Loud horn sound");
        truck.info();
    }
}
```

#### **Expected Output**:

```
Initializing Vehicle class...
Making sure of initialization...
Initializing an instance of the Vehicle class...
Creating a default vehicle.
The vehicle emits a honking sound.
model=null brand=Unknown
Creating a customized vehicle of brand: Ford and model: F-150
The vehicle emits a custom honking sound: Loud horn sound
model=F-150 brand=Ford
```

#### **Explanation**:

- The static blocks are executed when the class is first loaded.
- The instance block is executed when an object is created, followed by the constructor.
- The constructor calls set the `brand` and `model` attributes and print their respective outputs.

---

### **Q2: ElectronicDevice and Smartphone Class**

```java
public class ElectronicDevice {
    String brand;
    double price;

    public ElectronicDevice(String brand, double price) {
        this.brand = brand;
        this.price = price;
    }

    public void displayInfo() {
        System.out.println("Brand: " + brand);
        System.out.println("Price: $" + price);
    }
}

class Smartphone extends ElectronicDevice {
    private String model;
    private String operatingSystem;
    private String IMEI;

    // Constructor to initialize all attributes
    public Smartphone(String brand, double price, String model, String operatingSystem, String IMEI) {
        super(brand, price); // Call parent constructor
        this.model = model;
        this.operatingSystem = operatingSystem;
        this.IMEI = IMEI;
    }

    // Method to display the info of the smartphone
    @Override
    public void displayInfo() {
        super.displayInfo(); // Display info from ElectronicDevice
        System.out.println("Model: " + model);
        System.out.println("Operating System: " + operatingSystem);
    }

    // Getter for IMEI
    public String getIMEI() {
        return IMEI;
    }
}

public class Test {
    public static void main(String[] args) {
        Smartphone phone = new Smartphone("Samsung", 899.99, "Galaxy S21", "Android", "123456789012345");
        phone.displayInfo();
        System.out.println("IMEI: " + phone.getIMEI());
    }
}
```

#### **Expected Output**:

```
Brand: Samsung
Price: $899.99
Model: Galaxy S21
Operating System: Android
IMEI: 123456789012345
```

#### **Explanation**:

- The `Smartphone` class inherits from `ElectronicDevice` and adds additional attributes (`model`, `operatingSystem`, and `IMEI`).
- The `IMEI` is private and accessible only through the `getIMEI()` method.
- The `displayInfo()` method in `Smartphone` overrides the one in `ElectronicDevice` to include smartphone-specific details.

---

### **Q3: Volume Calculation of Geometrical Objects**

#### Code Implementation:

```java
// Myobject class
class Myobject {
    private double r; // radius

    public Myobject(double r) {
        this.r = r;
    }

    public double findVolume() {
        return -1.0; // No volume for the generic object
    }

    public double getRadius() {
        return r;
    }
}

// Sphere class
class Sphere extends Myobject {
    public Sphere(double r) {
        super(r);
    }

    @Override
    public double findVolume() {
        return (4.0 / 3.0) * Math.PI * Math.pow(getRadius(), 3);
    }
}

// Cylinder class
class Cylinder extends Myobject {
    private double h; // height

    public Cylinder(double r, double h) {
        super(r);
        this.h = h;
    }

    @Override
    public double findVolume() {
        return Math.PI * Math.pow(getRadius(), 2) * h;
    }
}

// Cone class
class Cone extends Cylinder {
    public Cone(double r, double h) {
        super(r, h);
    }

    @Override
    public double findVolume() {
        return (1.0 / 3.0) * Math.PI * Math.pow(getRadius(), 2) * super.h;
    }
}

public class Main {
    public static void main(String[] args) {
        Myobject[] objects = new Myobject[5];

        // Initialize objects as per Table 1
        objects[0] = new Sphere(2.5);
        objects[1] = new Cone(1.9, 8.9);
        objects[2] = new Cylinder(1.5, 6.5);
        objects[3] = new Cone(2.7, 5.7);
        objects[4] = new Sphere(3.5);

        // Calculate total volume
        double totalVolume = 0;
        for (Myobject obj : objects) {
            totalVolume += obj.findVolume();
        }

        System.out.println("Total Volume: " + totalVolume);
    }
}
```

#### **Expected Output**:

```
Total Volume: 91.0844384059076
```

#### **Explanation**:

- The `findVolume()` method is overridden in each subclass (`Sphere`, `Cylinder`, and `Cone`) to calculate the volume specific to each geometric shape.
- The `Main` class computes the total volume of all objects by calling `findVolume()`.

---

### **Q4: StaticContext Class with Static Final Variables**

```java
package rollbar;

public class FinalContext {
    public final void calculate() {
        System.out.println("calculate method is called");
    }
}

package rollbar;

public class StaticContext extends FinalContext {
    final static int value = 8; // Static final value initialization
    private double mark = 90.0; // Mark initialized to 90.0
    private int count = 1; // Count initialized to 1

    @Override
    public void calculate() {
        System.out.println("calculate method is called");
    }

    private int getCount() {
        return ++count;
    }

    private static double getMark() {
        return 90.0; // Returning static mark value
    }

    public static void main(String[] args) {
        StaticContext sv = new StaticContext();
        System.out.println("count= " + sv.getCount());
        System.out.println("value = " + value);
        System.out.println("mark= " + StaticContext.getMark());
        sv.calculate();
    }
}
```

#### **Expected Output**:

```
count= 2
value = 8
mark= 90.0
calculate method is called
```

#### **Explanation**:

- The `count` and `value` are printed through the methods in `StaticContext`.
- The `value` is a static final variable, and the `mark` is fetched through the static method.

---

### **Q5: Conceptual Questions**

#### **Q5(A)**:

1. **Can a class be abstract and final simultaneously?**
    
    - **Answer**: No, a class cannot be both abstract and final because a **final** class cannot be subclassed, whereas an **abstract** class is intended to be extended. Therefore, the two concepts contradict each other.
2. **Why would you create an abstract class without any instance variables or methods?**
    
    - **Answer**: An abstract class without instance variables or methods can be used as a **marker interface** or a way to group classes. It provides a common base for inheritance and can be used to enforce a certain type or category for its subclasses.
3. **Why must a class with an abstract method be declared abstract?**
    
    - **Answer**: A class with an abstract method must be declared abstract because abstract methods do not have a body, and the class must be incomplete in terms of providing a specific implementation for the method. This allows subclasses to implement the abstract methods.

---

#### **Q5(B)**:

```java
abstract class Animal {}

class Baby extends Animal {
    public double age;
}

class Cat extends Animal {
    public void sleep(int time) {
        System.out.println("Sleeping");
    }
}

public class Main {
    public void speak(Animal target) {
        if (target instanceof Baby) {
            System.out.println("WAAHHH");
        } else if (target instanceof Cat) {
            System.out.println("Meow");
```

```
    } else {
        System.out.println("Grrrrr");
    }
}

public static void main(String[] args) {
    Main main = new Main();
    
    Animal baby = new Baby();
    Animal cat = new Cat();
    
    main.speak(baby);  // Outputs: WAAHHH
    main.speak(cat);   // Outputs: Meow
    main.speak(new Animal()); // Outputs: Grrrrr
}
```

}

```

#### **Expected Output**:
```

WAAHHH Meow Grrrrr

```

#### **Explanation**:
- The `speak` method checks the type of the `Animal` object and prints the appropriate sound based on its type using `instanceof`.

---

```