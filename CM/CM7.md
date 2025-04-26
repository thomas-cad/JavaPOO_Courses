# Lecture 7

## Architecure

### The view

Allows the user to interact with the software, often made of windows

### The model

- It is where the data resides, made of one or more objects. It is the **Business logic layer**.
- It must contain everything to determine the **state** of the UI and the **data** displayed.

### The Controller

- The controller links the view and the model when a user action occurs on the view.
- This object is responsible for controlling the data in the model

## The observer-observable

### Pattern

![alt text](observer-observable_pattern.png)

Any modification to the model must be reflected in the view

### Interfaces

*Only for example `@Deprecated`*

```java
public interface Observer {
    void modelChanged ();
}
```

```java
public interface Observable {
    boolean addObserver ( Observer observer );
    boolean removeObserver ( Observer observer );
}
```

### Operation

- Any method that modifies the model (for example, setters) has been modified to notify the observers (views) so that they can refresh themselves. 

- The observer (the view-window FactoryViewer ) propagates the refresh message hierarchically to all its components (widgets) that need to be refreshed. 

The mechanism is **automated**.

### Controller

![alt text](controller.png)

The **direct observer-observable pattern** is preferred because it allows having multiple views on the same data