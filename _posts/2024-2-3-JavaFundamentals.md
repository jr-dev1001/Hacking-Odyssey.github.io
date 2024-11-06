---
layout: post
title: Learning Java Fundamentals 🔤!
subtitle: Windows 10/11 configuration theme with pink color scheme
excerpt_image: https://raw.githubusercontent.com/azzamimaf/pink-nadekosengoku/main/ss1.png
categories: windows theme
tags: [windows theme]
---

In this Blog we'll briefly learn about variables, datatypes, conditional statements, loops and functions in Java.

Let's start

<img src="/images/java_Fun.jpeg" height="300px" width="300px">

## Variables

Variables are containers for storing data values. In Java, variables must be declared with a specified data type before they can be used. Here are some common types of variables:

- **int**: Used for storing integer numbers.
- **double**: Used for storing floating-point numbers.
- **boolean**: Used for storing true/false values.
- **String**: Used for storing sequences of characters.
- **char**: Used for storing single characters.

Variables can also be declared as arrays to store multiple values of the same data type:

- **Array**: Used for storing multiple values of the same data type.

### Example:

```java
int num = 10;
double pi = 3.14;
boolean isTrue = true;
String name = "John";
char grade = 'A';

// Array declaration
int[] numbers = {1, 2, 3, 4, 5};
String[] fruits = {"Apple", "Banana", "Orange"};
```
In addition to the primitive data types mentioned above, Java also supports reference data types, which include objects and arrays. These reference data types store references to the actual objects or arrays stored elsewhere in memory.

### Example:

```java
// Object declaration
Person person = new Person("Alice", 25);

// Array declaration with reference data type
String[] names = new String[5];
```
## Conditional Statements

Conditional statements allow you to execute different blocks of code based on certain conditions. In Java, the common conditional statements are:

- **if**: Executes a block of code if a specified condition is true.
- **else**: Executes a block of code if the same condition as the `if` statement is false.
- **else if**: Allows you to specify a new condition if the previous condition is false.
- **switch**: Evaluates a variable and executes different blocks of code depending on its value.

### Example:

```java
int x = 10;

if (x > 0) {
    System.out.println("x is positive");
} else if (x < 0) {
    System.out.println("x is negative");
} else {
    System.out.println("x is zero");
}
```
## Loops

Loops are used to repeatedly execute a block of code as long as a specified condition is true. In Java, there are mainly three types of loops:

- **for loop**: Executes a block of code a specified number of times.
- **while loop**: Executes a block of code as long as a specified condition is true.
- **do-while loop**: Similar to a `while` loop, but the block of code is executed at least once before the condition is checked.

### Example:

```java
// Using a for loop
for (int i = 0; i < 5; i++) {
    System.out.println("Value of i: " + i);
}

// Using a while loop
int i = 0;
while (i < 5) {
    System.out.println("Value of i: " + i);
    i++;
}

// Using a do-while loop
int j = 0;
do {
    System.out.println("Value of j: " + j);
    j++;
} while (j < 5);
```
## Functions

Functions (or methods) are blocks of code that perform a specific task. They allow you to break your code into smaller, reusable parts. In Java, functions can be either static or non-static (instance) and can have a return type or be void (no return value).

### Example:

```java
// Non-static function with return type
public int add(int a, int b) {
    return a + b;
}
// Static function with no return type
public static void printMessage(String message) {
    System.out.println(message);
}
```

## In Next
In the upcoming blog, we'll learn OOPs concepts in day to day lives. Happy Learning!


