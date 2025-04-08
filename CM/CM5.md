# Lecture 5

## Asbstract

![alt text](abstract.png)

In this example, an object of the class LuxuryItem must necessarily be an
instance of the class TV or the class Computer. This type of class is called **an abstract class**, as opposed to
concrete classes like TV and Computer .

### Example

```java
public abstract class LuxuryItem extends Item {
    // ...
}
```

### Nota Bene

It is still possible to declare variables whose type is an abstract class. Nevertheless, only methods of a subclass can be used.

```java
LuxuryItem luxuryItem = new Computer ();
```

### Methods

```java
public abstract class Item {
    private final double netPrice ;

    public Item ( double netPrice ) {
        this . netPrice = netPrice ;
    }

    public final double getNetPrice () {
        return netPrice ;
    }

    public abstract double getVAT ();

    public final double getATIPrice () {
        return getNetPrice () + getVAT ();
    }
}
```