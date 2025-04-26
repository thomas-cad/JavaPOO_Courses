# Lecture 7

## Architecture

### The View

The view allows the user to interact with the software and is often composed of windows.

### The Model

- The model is where the data resides. It is made up of one or more objects and represents the **business logic layer**.
- It must contain everything needed to determine the **state** of the UI and the **data** displayed.

### The Controller

- The controller links the view and the model when a user action occurs on the view.
- This object is responsible for controlling the data in the model.

## The Observer-Observable Pattern

### Pattern

![Observer-Observable Pattern](observer-observable_pattern.png)

Any modification to the model must be reflected in the view.

### Interfaces

*For example, `@Deprecated`*

```java
public interface Observer {
    void modelChanged();
}
```

```java
public interface Observable {
    boolean addObserver(Observer observer);
    boolean removeObserver(Observer observer);
}
```

### Operation

- Any method that modifies the model (for example, setters) has been modified to notify the observers (views) so that they can refresh themselves.
- The observer (the view-window `FactoryViewer`) propagates the refresh message hierarchically to all its components (widgets) that need to be refreshed.
- The mechanism is **automated**.

### Controller

![Controller](controller.png)

The **direct observer-observable pattern** is preferred because it allows having multiple views on the same data.

---

### Points to Check:

1. **Images**: Ensure that the images `observer-observable_pattern.png` and `controller.png` are correctly integrated and visible.
2. **Concrete Examples**: If possible, add concrete examples to illustrate the use of the Observer-Observable pattern in a real application.
3. **Automation**: Briefly explain how this automation is implemented if necessary.