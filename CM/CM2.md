# Lecture 1

## `int` Type

- An `int` variable is always initialized to `0` by default if it is an instance variable (i.e., a field of a class). Local variables, however, are not initialized by default and must be explicitly initialized before use.

## Class Definition

To define a class:

```java
class Point {
    int xCoord;
    int yCoord;
}
```

## Reference Type

Firstly, we declare a variable that can hold a reference to an object of the `Point` class. This is a **reference type variable**.

```java
Point myPoint;
```

To create the object, it is necessary to use the keyword `new`:

```java
myPoint = new Point();
```

*Note: The variable `myPoint` contains a reference to the memory location storing the point's data.*

It is possible to combine both declaration and initialization:

```java
Point myPoint = new Point();
```

## Constructor

### Declaration

A constructor has the same name as the class and is used to initialize objects.

```java
Point(int xCoordInit, int yCoordInit) {
    xCoord = xCoordInit;
    yCoord = yCoordInit;
}

Point myPoint = new Point(23, 67);
```

### Overloading

It is possible to overload a constructor by declaring it multiple times with different parameter types or numbers. The constructor called depends on the types and number of arguments provided.

### `this` Keyword

- To call another constructor from within a constructor, use `this()`:

```java
Point(double rho, double theta) {
    this((int)(rho * Math.cos(theta)), (int)(rho * Math.sin(theta)));
}
```

- To refer to instance variables, use `this`:

```java
Point(int xCoord, int yCoord) {
    this.xCoord = xCoord;
    this.yCoord = yCoord;
}
```

## Methods

### Non-Intrusion Principle

A good practice in OOP is to avoid directly manipulating an object's state from outside the object. Instead, delegate operations to the object itself. This is known as the **Delegation Principle**.

### Static Variables

- **Class-Level Variables**: A static variable is shared among all instances of a class. There is only one copy of a static variable, regardless of how many objects are created.
- **Memory Efficiency**: Static variables are not tied to any particular instance, making them memory-efficient for shared data.
- **Access**: Static variables can be accessed directly using the class name, without needing an instance of the class.

```java
class Point {
    static int numberOfPoints = 0;
    int xCoord;
    int yCoord;

    Point(int xCoordInit, int yCoordInit) {
        xCoord = xCoordInit;
        yCoord = yCoordInit;
        numberOfPoints++;
    }

    void writeNumberOfPoints() {
        System.out.print("Number of points = ");
        System.out.print(numberOfPoints);
    }
}
```

### Static Methods

- **Class-Level Methods**: A static method belongs to the class rather than any specific instance. It can be called without creating an instance of the class.
- **No Access to Instance Variables**: Static methods cannot access instance variables or instance methods directly. They can only access other static members or call other static methods.
- **Utility Methods**: Static methods are often used for utility or helper methods that perform common tasks independent of instance data.

```java
class Point {
    static int numberOfPoints = 0;
    int xCoord;
    int yCoord;

    Point(int xCoordInit, int yCoordInit) {
        xCoord = xCoordInit;
        yCoord = yCoordInit;
        numberOfPoints++;
    }

    static void writeNumberOfPoints() {
        System.out.print("Number of points = ");
        System.out.print(numberOfPoints);
    }
}
```

## Running a Java Program

A Java program must always contain at least one class with a `main` method, which is the entry point of the program:

```java
public static void main(String[] args) {
    Point myPoint = new Point(10, 10);
    myPoint.writeCoordinates();
}
```