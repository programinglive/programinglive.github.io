---
layout: default
title: What is Abstract Class?
parent: Software Development
grand_parent: FAQ
description: "What is Abstract Class?"
---

# Abstract Class

**Table of Contents**
1. [Introduction](#introduction)
2. [What is an Abstract Class?](#what-is-an-abstract-class)
3. [Abstract Class vs Interface](#abstract-class-vs-interface)
4. [Benefits of Using Abstract Classes](#benefits-of-using-abstract-classes)
5. [How Abstract Classes Work](#how-abstract-classes-work)
6. [Examples of Abstract Classes in Code](#examples-of-abstract-classes-in-code)
7. [When to Use Abstract Classes](#when-to-use-abstract-classes)
8. [Best Practices for Using Abstract Classes](#best-practices-for-using-abstract-classes)
9. [Conclusion](#conclusion)

---

## Introduction
In object-oriented programming (OOP), an **abstract class** is a class that cannot be instantiated on its own but serves as a blueprint for other classes. It allows you to define methods and properties that can be shared by its subclasses while also providing the flexibility to define abstract methods, which the subclasses must implement.

Abstract classes are useful when you have a common base class that should provide some shared behavior but also need to ensure that specific methods are implemented by subclasses.

---

## What is an Abstract Class?
An **abstract class** is a class that may contain abstract methods (methods without implementation) as well as concrete methods (methods with implementation). It cannot be instantiated directly but must be subclassed by concrete classes that implement the abstract methods.

The key features of an abstract class are:
- **Abstract methods**: Methods that are declared but do not have a body or implementation in the abstract class. Subclasses must provide the implementation.
- **Concrete methods**: Methods that have a full implementation and can be inherited as-is by subclasses.
- **Shared functionality**: Abstract classes can define fields and methods that are common across multiple subclasses.

Example of an abstract class in Java:
```java
abstract class Animal {
    abstract void sound(); // abstract method

    void breathe() { // concrete method
        System.out.println("Breathing...");
    }
}
```

In this example, `sound()` is an abstract method, and `breathe()` is a concrete method.

---

## Abstract Class vs Interface
While both abstract classes and interfaces define a blueprint for other classes, there are several key differences between them:

### Key Differences:

- **Methods**:
    - An **abstract class** can have both abstract methods (without implementation) and concrete methods (with implementation).
    - An **interface** can only declare methods (without implementation) unless it's a modern interface with default methods (in languages like Java 8+).

- **Multiple Inheritance**:
    - A class can only inherit from **one abstract class** (single inheritance).
    - A class can implement **multiple interfaces**, allowing for multiple inheritances.

- **Fields**:
    - An **abstract class** can have instance variables (fields) and methods with or without implementation.
    - An **interface** cannot have instance variables, only constants (static final fields).

- **Constructors**:
    - An **abstract class** can have constructors, which can be called from the constructors of its subclasses.
    - An **interface** cannot have constructors.

### When to Use:

- Use **abstract classes** when you want to provide some shared implementation but still need certain methods to be implemented by subclasses.
- Use **interfaces** when you want to define a contract for behavior that multiple unrelated classes can implement.

---

## Benefits of Using Abstract Classes
Abstract classes provide several advantages in software design:

1. **Code Reusability**:  
   Abstract classes allow you to write common functionality in one place and reuse it in all subclasses, reducing code duplication.

2. **Enforced Inheritance**:  
   Abstract classes ensure that certain methods are implemented by subclasses, enforcing a clear structure and behavior across related classes.

3. **Encapsulation**:  
   By placing shared functionality in an abstract class, you can hide implementation details and only expose necessary methods to subclasses.

4. **Flexibility**:  
   Abstract classes provide a balance between full inheritance (as in concrete classes) and full abstraction (as in interfaces), making them versatile in design.

---

## How Abstract Classes Work
An abstract class cannot be instantiated directly, which means you cannot create an object of the abstract class itself. However, you can create objects of concrete subclasses that extend the abstract class. These subclasses are required to implement all the abstract methods defined in the abstract class.

### Example in Java:
```java
abstract class Shape {
    abstract void draw(); // abstract method

    void display() { // concrete method
        System.out.println("Displaying shape.");
    }
}

class Circle extends Shape {
    @Override
    void draw() {
        System.out.println("Drawing a circle.");
    }
}

class Rectangle extends Shape {
    @Override
    void draw() {
        System.out.println("Drawing a rectangle.");
    }
}

public class TestAbstract {
    public static void main(String[] args) {
        Shape circle = new Circle();
        circle.draw();  // Output: Drawing a circle.
        circle.display(); // Output: Displaying shape.

        Shape rectangle = new Rectangle();
        rectangle.draw();  // Output: Drawing a rectangle.
        rectangle.display(); // Output: Displaying shape.
    }
}
```

In this example, `Shape` is an abstract class, and both `Circle` and `Rectangle` are concrete subclasses that implement the `draw()` method.

---

## Examples of Abstract Classes in Code
### Example 1: **Vehicle Class**
An abstract class can represent a general concept, like a vehicle, where different types of vehicles implement the specific details of methods like `start()` and `stop()`.

```java
abstract class Vehicle {
    abstract void start();
    abstract void stop();

    void fuel() {
        System.out.println("Filling the tank...");
    }
}

class Car extends Vehicle {
    @Override
    void start() {
        System.out.println("Starting the car...");
    }

    @Override
    void stop() {
        System.out.println("Stopping the car...");
    }
}

class Bike extends Vehicle {
    @Override
    void start() {
        System.out.println("Starting the bike...");
    }

    @Override
    void stop() {
        System.out.println("Stopping the bike...");
    }
}
```

### Example 2: **Animal Behavior**
An abstract class can be used to model different animals, where the `sound()` method must be implemented by each specific animal.

```typescript
abstract class Animal {
    abstract makeSound(): void;

    sleep() {
        console.log("Sleeping...");
    }
}

class Dog extends Animal {
    makeSound() {
        console.log("Barking...");
    }
}

class Cat extends Animal {
    makeSound() {
        console.log("Meowing...");
    }
}
```

---

## When to Use Abstract Classes
Abstract classes should be used when you want to define a common base with shared functionality and force subclasses to provide their own specific implementations of abstract methods.

### Common Use Cases:
1. **Common Base for Related Classes**:  
   Use abstract classes when you have a group of related classes that share common methods but also need their own specific implementations.

2. **Avoiding Instantiation of a Class**:  
   If you want to prevent direct instantiation of a class, you can make it abstract, which forces the use of subclasses.

3. **Partial Implementation**:  
   When you have common functionality that should be shared across subclasses but still require certain methods to be customized, an abstract class is a good fit.

---

## Best Practices for Using Abstract Classes
1. **Keep It Simple**:  
   Only define methods in an abstract class that are common to all subclasses. Avoid overloading an abstract class with unnecessary functionality.

2. **Use Abstract Classes Sparingly**:  
   Abstract classes should be used when inheritance is appropriate. For other cases, interfaces might be a better choice.

3. **Favor Composition Over Inheritance**:  
   Whenever possible, prefer using composition (i.e., objects containing instances of other classes) over inheritance to create more flexible designs.

---

## Conclusion
Abstract classes play a significant role in object-oriented design by allowing you to define shared functionality while also enforcing the implementation of specific methods by subclasses. They strike a balance between full abstraction and full implementation, offering flexibility and reusability. Understanding when and how to use abstract classes effectively can greatly improve the maintainability and structure of your code.