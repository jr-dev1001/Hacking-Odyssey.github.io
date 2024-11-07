---
layout: post
title: Exploring Java Fundamentals Part 2 🔢!
subtitle: Why Object Oriented Programming? 
excerpt_image: 
categories: Java OOPS
tags: [Java OOPS]
---

"Innovation happens in the darndest places, and when you think it’s just a fad is often when it’s just about to change the world." - James Gosling
<div style="text-align:center;"> 
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/14/James_Gosling_2008.jpg/330px-James_Gosling_2008.jpg" alt="James Gosling">
</div>

# Understanding Object-Oriented Programming (OOPS) in Java

Hey there! Today, we're going to learn an important topic which is Object-Oriented Programming (OOPS) in Java.
But before we get started, let me ask you a question: Have you ever seen a car, a building, or a mobile phone? Of course, you have! Well, guess what? 
These everyday objects can actually help us understand the concept of OOPS in Java.

## What is Object-Oriented Programming (OOPS)?

OOPS is a programming paradigm based on the concept of "objects", which can contain data and code to manipulate that data. In simpler terms, it's like thinking about the world in terms of objects and their interactions.
OOPS is important in every programming language and in software lifecycle.

<div style="text-align:center;">
  <img src="https://github.com/jr-dev1001/jr-dev1001.github.io/assets/85192850/c63d566c-b709-4688-869f-409829b5a866" alt="image">
</div>


## Understanding OOPS with Analogies:

### 1. Car:

Imagine you have a car. Now, a car is made up of different parts like wheels, engine, seats, etc. Each part has its own unique function and properties. In OOPS, we can think of each part of the car as an "object". For example, the wheels can be one object, the engine another, and so on.

Now, let's say you want to drive the car. You don't need to know how each part works internally. All you need to know is how to use them. Similarly, in OOPS, objects have something called "methods" which are like actions that an object can perform. For example, the car object can have methods like start(), stop(), accelerate(), etc.
```java
// Car class
public class Car {
    // Attributes
    String color;
    String model;
    int speed;

    // Methods
    public void start() {
        System.out.println("The car has started.");
    }

    public void accelerate() {
        System.out.println("The car is accelerating.");
    }

    public void stop() {
        System.out.println("The car has stopped.");
    }
}
```

### 2. Building:

Think about a building. It has different floors, rooms, doors, and windows. Each floor has its own purpose, and each room serves a specific function. In OOPS, we can think of the building as a "class" and each floor, room, door, and window as "objects" belonging to that class.

Just like in a building, objects in OOPS can have properties (like color, size, etc.) and behaviors (like openDoor(), closeDoor(), etc.). These properties and behaviors are defined within the class and can be used by its objects.

```java
// Building class
public class Building {
    // Attributes
    int numFloors;
    int numRooms;

    // Methods
    public void openDoor() {
        System.out.println("The door is open.");
    }

    public void closeDoor() {
        System.out.println("The door is closed.");
    }
}
```

### 3. Mobile Phone:

Now, let's consider a mobile phone. A mobile phone has various features like making calls, sending messages, taking pictures, etc. Each feature represents a different functionality of the phone. In OOPS, we can think of the mobile phone as an "object" and each feature as a "method" of that object.

When you want to make a call, you don't need to know the inner workings of the phone. You just need to know how to use its features. Similarly, in OOPS, objects encapsulate data and methods, hiding the complex implementation details from the user.
```java
// MobilePhone class
public class MobilePhone {
    // Methods
    public void makeCall(String number) {
        System.out.println("Calling " + number);
    }

    public void sendMessage(String message, String recipient) {
        System.out.println("Sending message '" + message + "' to " + recipient);
    }
}
```

## In Next

In the upcoming blog, we'll delve into OOPs topics individually, exploring each one in detail. Happy Learning!
<div style="align:center;">
    <img src="https://media.tenor.com/G7PC6RSLXjgAAAAM/cat-work.gif" alt="CatWorkGIF">
</div>
