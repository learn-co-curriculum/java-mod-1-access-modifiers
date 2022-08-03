# Access Modifiers

## Learning Goals

- Explain what an access modifier is in Java.
- Explain when certain access modifiers should be used.

## Introduction

So far, we have seen quite a few keywords. For example, we have seen the `main` method pop up quite
frequently in the code that we write:

`public static void main(String[] args)`

In this lesson and the next few lessons, let us investigate this line some more.

For purposes of this lesson, we will focus more on the keyword `public` and what that means and how
it is an **access modifier**.

## What is an Access Modifier?

All of our classes and fields so far have either been `public` or have not
specified their level of visibility.

**Access modifiers** in Java let us specify the level of
access that classes, variables, methods and constructors should have.

The access levels are as follows:

1. `public` - Classes, variables, methods and constructors defined with this
   keyword are accessible by anyone.
2. `default` - This is the access modifier that is applied when an access modifier is not specified.
   It allows the variables, methods and constructors in a class to be visible to
   any other classes in the same package. More to come on what a package is later.
3. `private` - Any variables, methods and constructors defined with this keyword are
   only visible to the class where they are defined.

When specified, the access modifier must be the first part of the definition it
applies to. Let us look at our Bicycle class again:

```java
public class Bicycle {
    String color;
    int height;
}
```

`public class Bicycle` defines a public class, meaning anyone can access this class.

Notice that the variables `color` and `height` do not have an access modifier attached to them.
This means they have the default access modifier attached to them.

Let's look at each access modifier in more detail, from least restrictive to
most restrictive.

## Public

The `public` access modifier is the least restrictive access modifier. Classes, methods,
variables and constructors defined with this access modifier can be accessed from any other
class.

Since it is the most permissive access modifier, it should only be used for variables
and methods that are meant to be used by a wide range of other classes. As a
general principle, most variables should not be `public` and should instead be
made available through "accessor methods", so that additional logic can be added
to their handling without having to modify the code that accesses them.

`public main()`

## Default

The default access modifier is when no access modifiers are specified.

Classes, variables, methods and constructors defined without an access modifier are
available to all other classes in the same package.

If we go back to our `Bicycle` class example, the variables `color` and `height` both
use the default access level since the access modifier is not specified prior to the
data type. This means that we can make use of those variables even outside of the `Bicycle`
class as long as it is within the same package of the `Bicycle` class. Again, we will
discuss packages more in depth in a later lesson.

## Private

`private` is the most restrictive access modifier. Methods, variables and
constructors defined with this modifier can only be accessed within the class
where they are defined.

The `private` modifier is very useful in hiding implementation details of a
specific class from other classes that might use it. A very common pattern for
doing this is to define `private` variables and make their values accessible
through `public` methods, which when used in this way are usually called
"accessor methods".

We'll be learning about methods shortly, but for now, let us apply this knowledge to the
variables in the `Bicycle` class as an example.

```java
public class Bicycle {
   private String color;
   private int height;
}
```

The modification we made here is that we made the variables `color` and `height` private -
meaning that they can only be accessed within the `Bicycle` class. In a previous lesson, we
were able to access the properties using a syntax called "dot notation" in that we were able to
perform the following:

```java
Bicycle johnsBike = new Bicycle();
johnsBike.color = "blue";
johnsBike.height = 36;
```

To further explain dot notation, consider the line `johnsBike.color = "blue";`. We are accessing
the property `color` of the object `johnsBike` and trying to assign it to the word `blue`.

But with the `private` access modifier now attached to the properties, we would no longer be able
to access `color` or `height` outside of the class. We would have to find another way to access
these attributes.
