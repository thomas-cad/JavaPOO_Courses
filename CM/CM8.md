# Lecture 8

## Error handling

When the error occurs, Java creates an object of type Exception that contains information about the error. The exception travels up the sequence of method calls to the initial main method, it is the propagation to the `main()` method

## Types of error

- **Severe** : object of the `Exception` class
- **Handled by the programmer** : object of the `Exception` class
- **Related to the language** : object of the `RuntimeException` class a subclass of `Exception` class

All propagated errors are subclasses of the `Throwable` class

![alt text](exception_diagram.png)

## Error propagation
