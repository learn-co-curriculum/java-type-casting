# Type Casting

## Learning Goals

- Explain what casting is in Java and how it works

## What is Casting?

**Type casting** is a process that converts one data type into another data
type. For example, we could convert an `int` into a `double`, but we may
experience issues if we were to convert a `double` into an `int`. Let's review
the different types of data types along with primitive versus reference
variables for a minute.

### Review of Variables

If we remember back from our Variable lesson, there were 7 different primitive
data types that we discussed:

- `boolean`
- `byte`
- `char`
- `int`
- `long`
- `float`
- `double`

Each of the primitive data types were of varying different sizes and held
different types of data: true/false values, single characters, whole numbers,
and fractional numbers.

Reference variables are different in that they refer to an object, like
instances of our `Bicycle` class or the `Student` class. A `String` data type is
also considered a reference variable.

## How Casting Works

To see how casting works, let us look back at the Math class' `sqrt()` method.

`public static double sqrt(double a)`

The `sqrt()` method takes in a `double` data type as a parameter.
But when we call the method, we can pass as an argument an `int` data type such
as the value of 36 as shown below:

```java
double squareRoot = Math.sqrt(36);
```

Since a `double` data type is actually
required, Java will automatically convert the `int` value, 36, to the `double`
value of 36.0 _before_ passing the parameter to the `sqrt()` method. The method
will then eventually return a double value of 6.0 and store it within the
`squareRoot` variable. This type of casting is referred to as **widening** or
**upcasting**.

We might be thinking why? And how can Java do this automatically? Remember how
our different primitive data types have sizes? Well an `int` is only 4 bytes
whereas a `double` is 8 bytes. Since the `int` is smaller, we can easily cast it
as a `double`. It's like taking the contents from a smaller box and placing them
in a larger box - we know all the contents will definitely fit because they
originally fit in a smaller box; hence the names widening and upcasting.

Here is a list of valid promotions that we can upcast data types to:

![type cast promotions](https://curriculum-content.s3.amazonaws.com/java-mod-1/type-casting/Type-Casting-Promotions.png)

[Reference: Java How To Program (Early Objects), Tenth Edition](https://learning.oreilly.com/library/view/java-how-to/9780133813036/ch06lev1sec7.html#ch06lev1sec7)

This list shows us all the ways we can upcast certain data types. As we saw, an
`int` can be upcast to a `double`, but we can also upcast it to a `long` or a
`float`. Also notice that the `boolean` data type is excluded from this list as
it is not considered to be a number in Java.

Now what if we want to go the other way? What if, for some reason, we decide to
go from a `double` to an `int`? We need to be careful when doing so since that
kind of casting truncates the decimal part of the `double` value. The same
could be said if we decided to go from a `long` to an `int`, we may truncate
part of the value when doing so. But it can be done!

```java
int squareRoot = (int) Math.sqrt(36);
```

Since we know that `Math.sqrt(36)` will return a `double` with the value 6.0,
we can cast the 6.0 to an `int` data type by placing `(int)` in front of the
value we want to cast. This will force the compiler to jam the value of a
`double` into an `int`. This means the value of 6.0 will then become a 6 and be
assigned to the `int squareRoot`. This type of casting is referred to as
**narrowing** or **downcasting**.

As stated before, we need to be careful when downcasting because we could be
truncating the size so much that we lose information. Let's compare this to our
box example. If we take the contents out of a larger box and place them in a
smaller box, we do not know for sure if all the contents will fit. If the
contents do not all fit  in the smaller box, we may not be able to put all the
items into the smaller box - leaving some items completely out of a box.

A good example of when we might want to downcast is when we want to use the
`Math.random()` method to generate a random integer instead of a random
fractional number.

Consider rolling a die: a die has 6 sides with the numbers 1-6 on each face.

```java
int min = 1;
int max = 6;
int range = (max - min) + 1;

// Generate random numbers between 1 and 6
int randomRoll = (int)(Math.random() * range) + min;
```

To get a random integer value using the `random()` method, we need to define a
range first. In this case, we hardcoded the numbers 1 and 6 to define the range
of a standard die. Then we do a little math to ensure that a value between 1 and
6 is returned and cast it as an `int` to force the expression to return an
integer instead of a `double` since we are only concerned about the value before
the decimal point.


## Resources

[Java 17 Math](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Math.html)