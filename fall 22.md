

### Question 1: **Output of the `GoT` Program**

#### Code:

```java
public class GoT {
    {
        System.out.println("Valar dohaeris");
    }
    
    public String name;
    public String house;
    public double impact;
    public float intent;
    
    public GoT() {
        System.out.println("Best TV series after Breaking Bad");
    }
    
    public GoT(String name, String house) {
        this.name = name;
        this.house = house;
    }
    
    public GoT(double impact) {
        this("Daenerys", "Targaryen");
        this.impact = impact;
    }
    
    public GoT(float intent) {
        this("Arya", "Stark");
        this.intent = intent;
    }
    
    public void printFullName() {
        System.out.println(name + " " + house);
    }
    
    public void printDetails() {
        printFullName();
        System.out.println("Impact: " + impact);
        System.out.println("Intent: " + intent);
    }
    
    {
        System.out.println("Valar morghulis");
    }

    public static void main(String[] args) {
        GoT ob1 = new GoT();
        ob1.name = "John Snow";
        ob1.house = "404";
        
        GoT ob2 = new GoT(4.8);
        
        ob1.printDetails();
        ob2.printDetails();
    }
}
```

#### Explanation:

1. **Instance Initializers:** The blocks before constructors are instance initializer blocks. The first one prints "Valar dohaeris" and the second one prints "Valar morghulis".
    
    - These blocks will be executed **every time an object is created**, before the constructor is called.
2. **Constructor Execution:**
    
    - When `ob1` is created, the default constructor `GoT()` is called, which prints "Best TV series after Breaking Bad".
    - When `ob2` is created, the constructor `GoT(double impact)` is invoked. This calls the constructor `GoT(String name, String house)` with default values ("Daenerys", "Targaryen"), and then initializes `impact`.
3. **Object Details:**
    
    - For `ob1`, the details printed include the manually set `name` and `house`, and `impact` and `intent` are both 0.0 because they were not set.
    - For `ob2`, the details will include the default values "Daenerys Targaryen" and `impact = 4.8`, with `intent = 0.0` since it was not set.

#### Expected Output:

```
Valar dohaeris
Valar morghulis
Best TV series after Breaking Bad
John Snow 404
Impact: 0.0
Intent: 0.0
Daenerys Targaryen
Impact: 4.8
Intent: 0.0
```

---

### Question 2: **Movie Class with Required Access Modifiers and Methods**

#### Code Outline:

```java
public class Movie {
    private String name;
    protected String origin;
    public String genre;
    public float rating;
    
    // Constructor 1: All elements
    public Movie(String name, String origin, String genre, float rating) {
        this.name = name;
        this.origin = origin;
        this.genre = genre;
        this.rating = rating;
    }
    
    // Constructor 2: Only name and genre
    public Movie(String name, String genre) {
        this(name, "Unknown", genre, 0.0f);
    }

    // Method to get name
    public String getName() {
        return name;
    }

    // Method to get origin
    public String getOrigin() {
        return origin;
    }

    // Method to print details
    public void details() {
        System.out.println("You are watching " + name.toUpperCase());
        System.out.println("Origin: " + origin);
        System.out.println("Genre: " + genre);
        System.out.println("Rating: " + rating);
    }
}
```

#### Explanation:

1. **Access Modifiers:**
    
    - `name` is `private`, so it cannot be accessed directly from outside the class.
    - `origin` is `protected`, meaning it can be accessed within the same package or by subclasses.
    - `genre` and `rating` are `public`, so they can be accessed from anywhere.
2. **Constructors:**
    
    - The first constructor takes all four attributes.
    - The second constructor only takes `name` and `genre`, providing default values for `origin` and `rating`.
3. **Methods:**
    
    - `getName()` and `getOrigin()` are getter methods to access the private `name` and `origin` attributes from outside the class.
    - `details()` prints the details of the movie.

---

### Question 3: **Transport Classes with Modifications**

#### Code with Modifications:

```java
package transport;

public class Vehicle {
    private int noOfWheels;  // Private access modifier
    
    public Vehicle(int noOfWheels) {
        this.noOfWheels = noOfWheels;
    }

    // Getter for noOfWheels, making it read-only
    public int getNoOfWheels() {
        return noOfWheels;
    }
}

package publicTransport;

public class Bus extends Vehicle {
    private int licenseNo;

    public Bus(int licenseNo) {
        super(4);  // Assigning 4 wheels to the Bus
        this.licenseNo = licenseNo;
    }

    public int getLicenseNo() {
        return licenseNo;
    }

    public void setLicenseNo(int licenseNo) {
        this.licenseNo = licenseNo;
    }
}
```

#### Changes Made:

1. **Vehicle Class:**
    - `noOfWheels` is made `private` to prevent direct access.
    - The `getNoOfWheels()` method provides read-only access.
2. **Bus Class:**
    - The `licenseNo` remains `private` and has getter and setter methods for read and write access.

---

### Question 4: **Fifa, BrazilFans, ArgentinaFans Classes**

#### Code Outline:

```java
public class Fifa {
    protected int noOfGoals;
    protected String venue;
    protected int havingWorldCups;

    public Fifa() {
        System.out.println("Who will be winner?");
    }

    public Fifa(int noOfGoals, String venue) {
        this();
        this.noOfGoals = noOfGoals;
        this.venue = venue;
    }

    public void incrementWorldCups() {
        havingWorldCups++;
    }

    @Override
    public String toString() {
        return "[Fifa -> noOfGoals: " + noOfGoals + ", venue:" + venue + "]";
    }
}

public class BrazilFans extends Fifa {
    public BrazilFans(int noOfGoals, String venue, int havingWorldCups) {
        super(noOfGoals, venue);
        this.havingWorldCups = havingWorldCups;
    }

    @Override
    public String toString() {
        return "BrazilFans -> " + super.toString() + ", havingWorldCups:" + havingWorldCups;
    }
}

public class ArgentinaFans extends Fifa {
    public ArgentinaFans(int noOfGoals, String venue, int havingWorldCups) {
        super(noOfGoals, venue);
        this.havingWorldCups = havingWorldCups;
    }

    @Override
    public String toString() {
        return "ArgentinaFans -> " + super.toString() + ", havingWorldCups:" + havingWorldCups;
    }
}

public class Mid {
    public static void main(String[] args) {
        ArgentinaFans argentina = new ArgentinaFans(10, "Qatar", 2);
        BrazilFans brazil = new BrazilFans(7, "Qatar", 5);

        if (argentina.noOfGoals > brazil.noOfGoals) {
            argentina.incrementWorldCups();
        } else {
            brazil.incrementWorldCups();
        }

        System.out.println(argentina);
        System.out.println(brazil);
    }
}
```

#### Expected Output:

```
Who will be winner?
Argentina will win
Who will be winner?
Brazil will win
ArgentinaFans -> [Fifa -> noOfGoals: 10, venue:Qatar], havingWorldCups:2
BrazilFans -> [Fifa -> noOfGoals: 7, venue:Qatar], havingWorldCups:5
ArgentinaFans -> [Fifa -> noOfGoals: 10, venue:Qatar], havingWorldCups:3
BrazilFans -> [Fifa -> noOfGoals: 7, venue:Qatar], havingWorldCups:5
```

#### Explanation:

- **Constructor Call:** The `Fifa()` constructor prints "Who will be winner?" when any `Fifa` or subclass object is created.
- **Increment World Cups:** Depending on the `noOfGoals`, the respective team increments their World Cups.
- **Output Format:** The overridden `toString()` method provides the formatted output.

---
