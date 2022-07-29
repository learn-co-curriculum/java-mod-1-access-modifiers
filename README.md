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

# Access Modifiers

## Learning Goals

- Learning Goal 1
- Learning Goal 2

## Introduction

All of our classes and fields so far have either been `public` or have not
specific their level of visibility.

"Access modifiers" and special keywords in Java that let us specify the level of
access that classes, variables, methods and constructors should have.

The access levels are as follows:

1. "Default" - this is what happens in an access modifier is not specified, and
   it allows the variables, methods and constructors in a class to be visible to
   any other classes in the same package
2. "private" - variables, methods and constructors defined with this keyword are
   only visible to the class where they are defined. Note that only inner
   classes can be marked private, as outer classes are only useful if they can
   be used by other classes, so they have to be either "visible to the package"
   (default, i.e. no access modifier) or "public"
3. "public" - classes, variables, methods and constructors defined with this
   keyword are accessible by anyone
4. "protected" - classes, variables, methods and constructors defined with this
   keyword are only accessible by classes within the same package or subclasses

When specified, the access modifier must be the first part of the definition it
applies to. For example:

`private String sampleString` defines a private variable of type `String` with
the name `sampleString`

`private int sampleMethod(String param1, int param2) { return -1; }` defines a
private method named `sampleMethod` that return a value of type `int`

Let's look at each access modifier in more detail, from most restrictive to
least restrictive.

## Private

`private` is the most restrictive access modifier. Methods, variables and
constructors defined with this modifier can only be accessed within the class
where they are defined.

Outer classes and interfaces cannot be `private` since they would then become
impossible to use and therefore not useful for anything. Inner classes and
interfaces can be private, however, as they can then still be used inside the
outer class where they are defined.

The `private` modifier is very useful is hiding implementation details of a
specific class from other classes that might use it. A very common pattern for
doing this is to define `private` variables and make their values accessible
through `public` methods, which when used in this way are usually called
"accessor methods".

Let's consider a `Student` class as an example. At the beginning of our
implementation, we determine that a student's full name is made up of its first
name and last name and should be formatted as "<first-name> <space>
<last-name>", so we implement the `Student` class as follows:

```java
public class Student {
    private String firstName;
    private String lastName;

    public Student(String firstName, String lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
    }

    public String getFullName() {
        return firstName + " " + lastName;
    }
}
```

When someone comes to us and requests that the format of the full name be
changed to "<last-name>, <first-name>", we just need to change the
implementation of the `getFullName()` method to match the desired format, and we
don't have to worry that anyone is using our `firstName` and `lastName` fields
to format the student's full name in a different way because those fields are
`private` and cannot be accessed outside our class.

Here is the modified implementation of the `Student` class to format the full
name differently:

```java
public class Student {
    private String firstName;
    private String lastName;

    public Student(String firstName, String lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
    }

    public String getFullName() {
        return lastName + ", " + firstName;
    }
}
```

## Default

The default access modifier is when no access modifiers are specified and
results in different behavior for classes and interfaces:

1. For classes, variables and methods defined without an access modifier are
   available to all other classes in the same package
2. For interfaces, variables are implicitly `public`, `static` and `final` (we
   will cover what `static` and `final` mean in another section) and methods are
   implicitly `public` by default

## Protected

The `protected` access modifier makes variables, methods and constructors
defined with it accessible by any class in the same package, as well as any
class that extends the class where they are defined.

This is a good way to restrict access to "internal logic" only to classes that
have that specific kind of relationship to your own class, but still leave them
inaccessible to any other classes.

## Public

The `public` access modifier makes variables, methods and constructors defined
with it accessible from any other class.

It is the most permissive access modifier and should only be used for variables
and methods that are meant to be used by a wide range of other classes. As a
general principle, most variables should not be `public` and should instead by
made available through "accessor methods", so that additional logic can be added
to their handling without having to modify the code that accesses them.
