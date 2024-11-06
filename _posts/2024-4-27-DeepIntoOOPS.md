---
layout: post
title:  Dive Deep 🏊‍♂️ into OOPS with Java 🚀 
subtitle: What is in the OOPS?
excerpt_image: 
categories: Java OOPS
tags: [Java OOPS]
---

##

“Everyone in this country should learn how to program because it teaches you how to think” – Steve Jobs
<div style="text-align:center;"> 
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e5/Steve_Jobs_WWDC07.jpg/1200px-Steve_Jobs_WWDC07.jpg" width=500px height=500px "alt="Steve Jobs">
</div>

## Overview

In our last blog post, we took a broad look at Object-Oriented Programming (OOP) and its significance. Now, we're going to roll up our sleeves and dive into each topic within OOP, using Java as our tool.

### Table of Contents:
1. Class
2. Object
3. Four pillars of OOPS
    - Encapsulation
    - Abstraction
    - Inheritence
    - Polymorphism


## Class: The Blueprint 📝

A class in Java is like a blueprint or a template for creating objects. It defines the properties (attributes) and behaviors (methods) that each object of that class will have. 

```java
public class Car {
    // Properties
    private String make;
    private String model;
    private int year;

    // Constructor
    public Car(String make, String model, int year) {
        this.make = make;
        this.model = model;
        this.year = year;
    }

    // Behaviors
    public void start() {
        System.out.println("The " + year + " " + make + " " + model + " is starting.");
    }
}
```

## Object: Bringing Classes to Life 🚗

An object is an instance of a class. When you create an object, you're essentially creating a specific realization of the class blueprint. Each object has its own set of properties and can perform actions defined by the class methods.

```java
public class Main {
    public static void main(String[] args) {
        // Creating an object of the Car class
        Car myCar = new Car("Toyota", "Mercedes", 2024);
        
        // Calling the start method on the object
        myCar.start();
    }
}
```

## The Four Pillars of OOP

### Encapsulation: Data hiding and Access Control(Wrapping It Up) 🎁

Encapsulation is about bundling data (attributes) and methods (behaviors) together within a class and controlling access to them. It helps in achieving data hiding, where the internal state of an object is hidden from the outside world.

```java
public class Car {
    // Properties
    private String make;
    private String model;
    private int year;

    // Constructor and methods remain the same...
}
```

### Abstraction: Focus on What Matters 🧠

Abstraction is the process of hiding the complex implementation details and showing only the essential features of an object. It allows us to focus on what an object does rather than how it does it. 

### Abstract Class:

```java
public abstract class Vehicle {
    // Abstract method
    public abstract void start();
}

public class Car extends Vehicle {
    // Implementing the abstract method
    @Override
    public void start() {
        System.out.println("Car is starting...");
    }
}
```

### Interface:

```java
public interface Vehicle {
    // Method declaration
    void start();
}

public class Car implements Vehicle {
    // Implementing the interface method
    @Override
    public void start() {
        System.out.println("Car is starting...");
    }
}
```

## Inheritance: Reusing and Extending Code (Passing Down Knowledge) 📚

Inheritance is a mechanism where a new class (subclass) is created from an existing class (superclass). The subclass inherits the properties and behaviors of the superclass and can also have its own additional features.

```java
// Superclass
public class Vehicle {
    public void start() {
        System.out.println("Vehicle is starting...");
    }
}

// Subclass
public class Car extends Vehicle {
    // Additional methods specific to Car...
}
```

## Polymorphism: Many Forms of Behavior (Many Forms, One Concept) 🔄

Polymorphism allows objects of different classes to be treated as objects of a common superclass. It enables methods to be implemented differently in derived classes.

### Method Overriding:

```java
// Superclass
public class Vehicle {
    public void start() {
        System.out.println("Vehicle is starting...");
    }
}

// Subclass
public class Car extends Vehicle {
    // Overriding the start method
    @Override
    public void start() {
        System.out.println("Car is starting...");
    }
}
```

### Method Overloading:

```java
public class Calculator {
    // Method with different parameter lists
    public int add(int a, int b) {
        return a + b;
    }

    public double add(double a, double b) {
        return a + b;
    }
}

```

And there you have it! We've explored the basics of OOP in Java. Keep experimenting and practicing to solidify your understanding. If you have any questions or topics you'd like us to delve into further, feel free to reach out! 🚀

## In Next
In the next blog we will be learning `interfaces` in java.
<div style="align:center;">
    <img src="/images/Blog4_ending.jpg" width="150px" height="150px" alt="Chimp learning interface in java">
</div>

