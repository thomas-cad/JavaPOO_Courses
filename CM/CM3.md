# Lecture 3

---

## Visibility

4 types available:

- `public`: Visible to everyone
- `private`: Only visible within the class
- `package` (**default value**): Only accessible by classes in the same package
- `protected`: Only accessible by subclasses or from the same package

Example :

```java
class Point {
    private int xCoord;
    private int yCoord;
}
```

### Encapsulation

When attributes are declared as private, data cannot be read or edited directly. To read the data, use a **getter** declared as `public`, and to edit the data, use a **setter** declared as `public`.

A setter allows you to check the validity, coherence, and integrity of the data structure. Additionally, it is essential to maintain the application's consistency by triggering a refresh of the data where it used when changes are made.

## Interface

The collection of methods used to communicate with other objects is called **Interface**. These methods must be *public*, and attributs *private*. They allow to modify the implementation of a method transparently. The data has to be properly *encapsulated*.

## Package

It is a collection of classes, they are grouped by their purpose (e.g. IO, Network Communication, UI, ...). Classes higly dependent of each other : **strong coupling** are grouped in the same package, ones with feew dependencies and different purpose : **weak coupling** are in different packages. This principia allows to facilitate the reuse.

### Delaration

```java
package fr.tp.geometry.model;

class Point {
    private int xCoord ;
    private int yCoord ;

    public Point (int xCoord, int yCoord ) {
        this . xCoord = xCoord ;
        this . yCoord = yCoord ;
    } // ...
}
```

A package **can contains other package**. The class file will be stored in a subdirectory that follows the same structure as the one defined by the package name. The dots ( . ) are replaced by slashes ( / ) (e.g. path: ../src/fr/tp/geometry/model/Point.java)

### Importation

To access to a class from another package you have to specify the package name.

```java
package fr.tp. geometry . editor ;

public class Main {
    public Main () {
    } // This default constructor is not really needed to explicit

    public static void main ( String [] args ) {
        fr.tp.geometry.model.Point myPoint = new fr.tp.geometry.model.Point (10 , 10);
        myPoint.writeCoordinates ();
    }
}
```

To import a package use the keyword `import package_name` and to import all classes from a package `ìmport package_name.*`

## Strings

```java
String str1 = null ; // Initialized with the null value
String str2 = " Java "; // Initialized with a reference
```

### Concatenation

```java
String str1 = " Java ";
String str2 = " coffee ";
String str3 = str1 + " " + str2 ;
```

**Or**

```java
String str4 = str1 . concat ( str2 );
```

## Equality Operator `==

Works with discrete scalar types : `char , byte , short , int , long , boolean`

For references types, the operator checks with both var refer to the same object in memory.

In a broader sense, to check if two objects are equal, classes offer `equal()` method.

## ArrayList<E>

List of reference to E instances, Initialized to empty.

```java
ArrayList <Robot > myRobots = new ArrayList <Robot >();
```

### Methods

- **`add(E eObject)`**: Adds an element to the end of the list.
  ```java
  List<String> list = new ArrayList<>();
  list.add("Apple"); // List becomes ["Apple"]
  ```

- **`add(int index, E eObject)`**: Inserts an element at a specific position.
  ```java
  List<String> list = new ArrayList<>(Arrays.asList("Banana", "Cherry"));
  list.add(1, "Apple"); // List becomes ["Banana", "Apple", "Cherry"]
  ```

- **`remove(int index)`**: Removes the element at a specific position.
  ```java
  List<String> list = new ArrayList<>(Arrays.asList("Banana", "Apple", "Cherry"));
  list.remove(1); // List becomes ["Banana", "Cherry"]
  ```

### `for` loop

```java
ArrayList <Robot > myRobots = new ArrayList <Robot >();
myRobots .add(/* ... */);
// ...

for (int index = 0; index < myRobots.size(); index++) {
    Robot myRobot = myRobots.get(index);
    System .out. println (myRobot);
    // ...
}
```

```java
ArrayList <Robot > myRobots = new ArrayList <Robot >();
myRobots .add(/* ... */);
// ...

for (Robot myRobot : myRobots) {
    System .out. println (myRobot);
    // ...
}
```