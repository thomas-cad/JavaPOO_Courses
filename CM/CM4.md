# Lecture 4

![Inheritance schema](InheritanceSchema.png)  

- The **child class** can also be called a **subclass**, and the **parent class** can be referred to as the **superclass**.  

## Principles of Inheritance  

### 1. Enrichment (Modular Extension)  
Enriching a child class by adding new **attributes** and **methods** that were not present in the parent class.  

### 2. Redefinition (Substitution)  
Redefining an inherited method by providing a new implementation in the child class.  

### Examples  

#### Method Overriding  
```java  
public class LuxuryItem extends Item {  
    @Override  
    public double getVAT() {  // Method overriding  
        return 0.33 * getNetPrice();  // 33% tax rate  
    }  
    // ...  
}  
```  

#### Attribute Extension  
```java  
public class Television extends LuxuryItem {  
    private int voltage;  
    private int screenSize;  

    public int getVoltage() {  
        return voltage;  
    }  

    public int getScreenSize() {  
        return screenSize;  
    }  
    // ...  
}  
```  

### Root of the Inheritance Tree  
- If a class does not explicitly specify a parent class, it **implicitly inherits** from the `Object` class in the `java.lang` package.  
- Java supports **single inheritance**, meaning a class can inherit from **only one** parent class.  

## Constructors in Inheritance  
If the parent class has constructors, the child class **must call one of them** using `super()`. This call **must be the first instruction** in the child constructor.  

#### Example  
```java  
public class ColouredPoint extends Point {  
    private Color color;  

    public ColouredPoint(int xCoord, int yCoord, Color color) {  
        super(xCoord, yCoord);  // Must be the first instruction  
        this.color = color;  
    }  
}  
```  

## Polymorphism  
An object instantiated from a subclass has **multiple types** (its own type and all ancestor types). This is called **polymorphism**.  

## Method Binding  

### 1. Static Binding  
- The compiler determines the method to call **at compile time** based on the **variable type**.  

### 2. Dynamic Binding  
- The actual method is resolved **at runtime** based on the **object's real type**.  

### Java’s Approach  
- Java uses **dynamic binding** for method calls, making it a **dynamically-bound** language.  

### Useful Methods from `Object`  

#### `getClass()`  
Returns the **runtime class** of an object.  
```java  
System.out.println(shape.getClass());  
```  

#### `toString()`  
Used by `System.out.print()` to convert an object to a string.  
```java  
System.out.print(myRobot);  // Calls myRobot.toString()  
```  

## The `final` Keyword  

### 1. Final Methods  
- A `final` method **cannot be overridden** in subclasses.  
- Ensures **compile-time binding** (no runtime ambiguity).  

### 2. Final Classes  
- A `final` class **cannot be extended** (no inheritance allowed).  
- Example: The `String` class in Java is `final`.  

### 3. Final Attributes  
- A `final` attribute is **immutable** (cannot be modified after initialization).  