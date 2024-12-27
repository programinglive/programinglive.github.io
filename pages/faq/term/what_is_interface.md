---
layout: default
title: What is an Interface in Programming?
parent: Term
grand_parent: FAQ
description: "What is an Interface in Programming?"
---

# Interface

**Table of Contents**

1. [Introduction](#introduction)
2. [What is an Interface?](#what-is-an-interface)
3. [Interfaces in Programming Languages](#interfaces-in-programming-languages)
4. [Benefits of Using Interfaces](#benefits-of-using-interfaces)
5. [How Interfaces Work](#how-interfaces-work)
6. [Interface vs Abstract Class](#interface-vs-abstract-class)
7. [Examples of Interfaces in Code](#examples-of-interfaces-in-code)
8. [Best Practices for Using Interfaces](#best-practices-for-using-interfaces)
9. [Conclusion](#conclusion)

---

## Introduction

In object-oriented programming (OOP), an **interface** is a type that defines a contract for classes that implement it.
It specifies a set of methods (or properties) that a class must provide, but it doesn't contain the implementation
details. This allows different classes to implement the same interface in their own way while maintaining a consistent
structure.

Interfaces are fundamental in ensuring that different components or modules in a system can interact with each other in
a predictable way, promoting flexibility, reusability, and maintainability in code.

---

## What is an Interface?

An **interface** is a collection of abstract methods (or properties) that define a set of behaviors that a class must
implement. It essentially acts as a blueprint for classes. The key characteristic of an interface is that it only
provides method signatures (without implementation) and does not contain any logic or state. Classes that implement the
interface must provide their own implementation of the methods defined by the interface.

For example, in many programming languages like Java, C#, and TypeScript, interfaces are used to define common behaviors
that different classes can share.

---

## Interfaces in Programming Languages

Here’s how interfaces are used in different programming languages:

### 1. **Java**

In Java, an interface is defined using the `interface` keyword. A class implements an interface using the `implements`
keyword. The class must then provide implementations for all the methods declared in the interface.

Example in Java:

```java
interface Animal {
    void speak();
    void eat();
}

class Dog implements Animal {
    @Override
    public void speak() {
        System.out.println("Woof!");
    }

    @Override
    public void eat() {
        System.out.println("Eating dog food.");
    }
}
```

### 2. **C#**

In C#, interfaces are defined similarly to Java, using the `interface` keyword. A class implements an interface with the
`: interfaceName` syntax.

Example in C#:

```csharp
public interface IAnimal {
    void Speak();
    void Eat();
}

public class Dog : IAnimal {
    public void Speak() {
        Console.WriteLine("Woof!");
    }

    public void Eat() {
        Console.WriteLine("Eating dog food.");
    }
}
```

### 3. **TypeScript**

In TypeScript, interfaces are used to define object shapes and class methods. Classes that implement an interface must
adhere to the structure outlined by the interface.

Example in TypeScript:

```typescript
interface Animal {
  speak(): void;

  eat(): void;
}

class Dog implements Animal {
  speak() {
    console.log("Woof!");
  }

  eat() {
    console.log("Eating dog food.");
  }
}
```

---

## Benefits of Using Interfaces

Using interfaces in programming offers several advantages:

1. **Decoupling**:  
   Interfaces help decouple the implementation details from the interface's usage. This separation makes it easier to
   change the implementation without affecting the rest of the system.

2. **Polymorphism**:  
   Interfaces enable polymorphism, allowing different classes to be treated interchangeably if they implement the same
   interface. This facilitates flexible and reusable code.

3. **Code Reusability**:  
   By defining a common interface, you can ensure that different classes can be used in the same way, leading to better
   code reusability.

4. **Improved Maintainability**:  
   When a system follows an interface-based design, it is easier to maintain and extend. New classes can be added as
   long as they implement the appropriate interfaces, without modifying existing code.

5. **Enforcing Standards**:  
   Interfaces enforce a standard structure for implementing specific functionality, ensuring consistency across
   different parts of an application.

---

## How Interfaces Work

When a class implements an interface, it must provide concrete implementations for all the methods defined in that
interface. This guarantees that the class follows the contract laid out by the interface. Here’s a breakdown of how
interfaces work:

1. **Definition**:  
   An interface defines the methods and properties that must be implemented by any class that chooses to implement the
   interface.

2. **Implementation**:  
   A class that implements the interface provides the actual implementation for the methods and properties defined by
   the interface. This means the class will provide the logic for each method declared in the interface.

3. **Polymorphism**:  
   When different classes implement the same interface, they can be treated polymorphically. This means they can be used
   interchangeably if they are expected to follow the same contract.

---

## Interface vs Abstract Class

While both interfaces and abstract classes provide a blueprint for other classes to follow, there are some important
differences between the two:

### Key Differences:

- **Methods**:
    - An **interface** can only declare method signatures without any implementation.
    - An **abstract class** can have both abstract methods (without implementation) and concrete methods (with
      implementation).

- **Multiple Inheritance**:
    - A class can implement **multiple interfaces**, which allows for multiple inheritances.
    - A class can only inherit from **one abstract class** (single inheritance).

- **Fields/Properties**:
    - An **interface** cannot have any fields or properties (though it can define properties as method signatures).
    - An **abstract class** can have fields, properties, and static methods.

### When to Use:

- Use **interfaces** when you want to define a contract for behavior that can be implemented by multiple, potentially
  unrelated classes.
- Use **abstract classes** when you need to provide a common base with shared implementation and still enforce certain
  methods to be implemented by subclasses.

---

## Examples of Interfaces in Code

Here’s how interfaces work in various contexts:

### Example 1: **Database Connection**

An interface for database connections could define methods for opening and closing a connection, regardless of the type
of database (MySQL, MongoDB, etc.).

```java
interface DatabaseConnection {
    void openConnection();
    void closeConnection();
}

class MySQLConnection implements DatabaseConnection {
    @Override
    public void openConnection() {
        System.out.println("Connecting to MySQL...");
    }

    @Override
    public void closeConnection() {
        System.out.println("Closing MySQL connection...");
    }
}

class MongoDBConnection implements DatabaseConnection {
    @Override
    public void openConnection() {
        System.out.println("Connecting to MongoDB...");
    }

    @Override
    public void closeConnection() {
        System.out.println("Closing MongoDB connection...");
    }
}
```

### Example 2: **Shape Area Calculation**

In this example, different shape classes implement an interface for calculating the area of various geometric shapes.

```typescript
interface Shape {
  calculateArea(): number;
}

class Circle implements Shape {
  radius: number;

  constructor(radius: number) {
    this.radius = radius;
  }

  calculateArea(): number {
    return Math.PI * this.radius * this.radius;
  }
}

class Rectangle implements Shape {
  width: number;
  height: number;

  constructor(width: number, height: number) {
    this.width = width;
    this.height = height;
  }

  calculateArea(): number {
    return this.width * this.height;
  }
}
```

---

## Best Practices for Using Interfaces

1. **Use Interfaces for Contracts**:  
   Always use interfaces to define clear contracts for classes that implement certain behaviors, ensuring consistency
   and predictability across your code.

2. **Keep Interfaces Small and Focused**:  
   A good interface should have a single responsibility. Avoid creating "fat" interfaces with too many methods. Stick to
   the interface segregation principle.

3. **Prefer Interfaces Over Abstract Classes**:  
   When possible, prefer interfaces over abstract classes to allow for multiple inheritances and better decoupling of
   your code.

4. **Use Interfaces for Dependency Injection**:  
   Interfaces work well in dependency injection scenarios, as they allow the implementation to be easily swapped out.

---

## Conclusion

Interfaces are a powerful tool in object-oriented programming that help define clear contracts for classes to follow.
They promote code reusability, flexibility, and maintainability by decoupling interfaces from their implementation.
Understanding how to use interfaces effectively can improve the structure and scalability of your applications, making
your code more modular and easier to maintain.  