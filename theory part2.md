### **OOP Concepts: Sorted Notes**

---

### **1. Class and Object Basics**

- **Class**: Blueprint for objects (contains fields and methods).
- **Object**: Instance of a class.
- **Constructors**:
    - **Default**: No parameters, initializes default values.
    - **Parameterized**: Accepts arguments to initialize specific values.
- **Instance Variables**: Belong to each object.
- **Instance Methods**: Operate on instance variables.
- **Static Context**:
    - **Static Variable**: Shared among all objects.
    - **Static Method**: Belongs to the class, can't access instance variables directly.
    - **Static Block**: Runs once when the class is loaded.

---

### **2. Inheritance**

- **`extends`**: Allows a class to inherit fields and methods from another class.
- **`super`**:
    - Access parent methods: `super.methodName()`.
    - Call parent constructors: `super(args)`.
- **Method Overriding**: Child class redefines a parent method with the same signature.

---

### **3. Encapsulation**

- **Access Modifiers**:
    - **Private**: Accessible only within the class.
    - **Protected**: Accessible in the package and subclasses.
    - **Public**: Accessible everywhere.
- **Getters and Setters**: Control access to private variables.

---

### **4. Polymorphism**

- **Method Overloading**: Same name, different parameters.
- **Method Overriding**: Redefining parent methods in child classes.
- **Runtime Polymorphism**: Parent reference for child object (e.g., `Parent obj = new Child();`).

---

### **5. Abstract Classes**

- **Abstract Class**: Cannot be instantiated; may contain abstract and concrete methods.
- **Abstract Methods**: Declared without implementation; must be implemented in subclasses.

---

### **6. Static Context**

- **Static Variable**: Shared memory, belongs to the class.
- **Static Method**: Called without creating an object.
- **Static Block**: Executes once when the class is loaded.
- **Instance Block**: Executes each time an object is created.

---

### **Key Keywords**

- **`this`**: Refers to the current object.
- **`super`**: Refers to the parent class.
- **`final`**:
    - Final Variable: Can't be reassigned.
    - Final Method: Can't be overridden.
    - Final Class: Can't be inherited.

---

