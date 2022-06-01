# Keywords

## Learning Goals

- Explain what keywords are in Java
- Name the common keywords 

## Introduction

When we define class, methods and variables, we can specify additional properties that will tell Java how we intend to 
use them. For now, we are going to focus on the additional properties on the default `main()` method in Java: 

`public static void main(String[] args)`

Let's build up this method signature, one element at a time: 

## `public`

A `public` method or variable means that it can be accessed by anyone who has access to the class. We will learn more about 
access modifiers in later units, but for now this means that our `main` method can be accessed by any other class in our program, 
including the JVM itself. 

`public main()`

## `static` 

A `static` member of a class (i.e. a variable or a method) is a member that can be accessed directly on the class without needing 
an instance of that class to be created. This is usually the case when you describe something about the class that will 
be true for all instances of that class. 

In our previous `Bicycle` class, we could have a variable `numWheels` that represents the number of wheels that a bicycle 
has, and we could say it's `static` because all our bikes will always have exactly two wheels. Here is the `Bicycle` class 
with the `numWheels` variable added: 

```java 
public class Bicycle {
    String color; 
    int height; 
    int position; 
    static numWheels; 
} 
```

In Java, any class that you want to be able to run from the command line needs to have a `public` (i.e. fully accessible) 
`static` (i.e. accessible through the class, without an object) method called `main`

`public static main()`

## `void`

When we call a method, that method will execute its instructions, and we might expect something to happen as a result. 
We will go over return types in a later unit, but for now we just need to know that `void` is a special kind of return type in 
Java that means that the method does not return anything. The `main` method never returns anything because it's the first method 
that gets called in any program and therefore does not have anyone to return anything to. 

`public static void main()`

## `args`

Lastly, the default `main()` method in Java takes an array of `String` values as a parameter. An "array" is a collection of variables - 
it can be used when we want to refer to more than one thing of the same type: 

`String[] sampleArray`

An array is defined in Java by adding `[]` after the type definition, which defines a collection of objects of that type. In the example 
above, we defined an array of objects of type `String` and we called the collection `sampleArray`. 

The `String` array for the `main` method is usually called `args` because it represents the arguments that can be passed into your 
program when it's run from the command line. We will learn more about that in a later unit, so we can ignore the `args` variable 
for now, although it does need to be part of our method definition for `main`: 

`public static void main(String[] args)` 
