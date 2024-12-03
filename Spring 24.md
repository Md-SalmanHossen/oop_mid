
---

### **Question 1: Point2D and Point3D Classes**

#### I. Completing the `Display` Method in `Point2D`:

```java
public String Display() {
    return "x = " + x + ", y = " + y;
}
```

#### II. Adding a Constructor in `Point3D`:

```java
public Point3D(int x, int y, int z) {
    super(x, y); // Call the base class constructor
    this.z = z;
    System.out.println("Point3D constructor");
}
```

#### III. Adding Another `Display` Method in `Point3D`:

```java
@Override
public String Display() {
    return super.Display() + ", z = " + z;
}
```

#### Final Code:

```java
class Point2D {
    int x, y;

    public Point2D(int x, int y) {
        this.x = x;
        this.y = y;
        System.out.println("Point2D constructor");
    }

    public String Display() {
        return "x = " + x + ", y = " + y;
    }
}

class Point3D extends Point2D {
    int z;

    public Point3D(int x, int y, int z) {
        super(x, y); // Calls Point2D constructor
        this.z = z;
        System.out.println("Point3D constructor");
    }

    @Override
    public String Display() {
        return super.Display() + ", z = " + z;
    }
}

public class Test {
    public static void main(String[] args) {
        Point2D p2D = new Point2D(1, 2);
        System.out.println(p2D.Display());
        Point3D p3D = new Point3D(5, 4, 3);
        System.out.println(p3D.Display());
    }
}
```

#### **Expected Output**:

```
Point2D constructor
x = 1, y = 2
Point2D constructor
Point3D constructor
x = 5, y = 4, z = 3
```

---

### **Question 2: Myparent and Mychild Classes**

#### **Corrected Code**:

1. **Adding the `myroot()` Method** in `Myparent`:

```java
public double myroot() {
    return Math.sqrt(p);
}
```

2. **Correcting Constructor in `Mychild`**:

```java
public Mychild(int K) {
    super(); // Calls the parent class constructor
    set_p(K); // Initialize 'p' using the setter
}
```

3. **Correcting the `Mytest` Class**:

```java
public class Mytest {
    public static void main(String[] args) {
        Myparent c1 = new Mychild(2);
        Myparent c2 = new Mychild(3);
        c2.set_p(4);

        int x = c2.myfunction();
        double y = ((Mychild) c1).myroot();

        System.out.println("x = " + x + ", y = " + y);
    }
}
```

#### **Expected Output**:

```
x = 16, y = 1.4142135623730951
```

---

### **Question 3: Output of `Person` Class**

#### Code:

```java
class Person {
    int id;
    String name;
    static int s = 10;

    {
        System.out.println("3");
    }

    public Person() {
        this.id = 1;
        this.name = "M";
        System.out.println("1");
        s++;
    }

    public Person(int id, String name) {
        this();
        this.id = id;
        this.name = name;
        System.out.println("2");
        s++;
    }

    public static void main(String args[]) {
        Person p = new Person(1, "N");
        Person p1 = new Person();
        System.out.println(p1.s);
        p.s = 11;
        System.out.println(Person.s);
    }
}
```

#### **Expected Output**:

```
3
1
2
3
1
11
11
```

#### **Explanation**:

- The static variable `s` is incremented each time a constructor is called.
- The initializer block runs before the constructor.

---

### **Question 4: Calculating Total Purchase Price**

#### Main Method:

```java
public class MyTest {
    public static void main(String[] args) {
        FoodItem veg = new Vegetable("Cauliflower");
        veg.setparameter();
        double vegPrice = veg.getprice(2); // 2 Kg of Cauliflower

        FoodItem fish = new Fish("small");
        fish.setparameter();
        double fishPrice = fish.getprice(3); // 3 Kg of small fish

        System.out.println("Total Price: " + (vegPrice + fishPrice));
    }
}
```

#### **Expected Output**:

```
Total Price: 1050.0
```

#### **Explanation**:

1. **Vegetable (Cauliflower)**:
    
    - `c = 25`, `z = 18%`
    - Price for 2 Kg: `25 * 2 * (1 + 18/100) = 59.0`
2. **Fish (small)**:
    
    - `c = 200`, `z = 25%`
    - Price for 3 Kg: `200 * 3 * (1 + 25/100) = 750.0`
3. Total: `59.0 + 750.0 = 1050.0`
    

---

