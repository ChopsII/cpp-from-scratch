# Lesson 2: objects, variables, constants and expressions

Last lesson, we made a program that prints "Hello, World!" to the screen.

It's a good idea to start each lesson by trying to redo any exercises or examples from the previous lesson from memory, looking back only when you need to, and continuing to do so each lesson for each exercise or example until you can write them from memory.

With that in mind, please try to write a program to write "Hello, World!" to the screen again.

I will try to list exercises and examples in a way that restates their requirements without giving away the code, so that you don't have to remember all the exercises and examples, you just have to learn how to implement them.

## *objects*

One of the fundamental ideas in C++ is the idea of the *object*. Any "thing" in C++ is an object, or more correctly, any data that acts like one logical entity is an object.

Objects can take many many forms, we'll slowly get exposed to many of these throughout this course.

Objects may have names, or they may not.

We've already encountered one named object in the previous lesson, do you know what it is?
If not, we will see it again soon; point it out when you do see it.

Objects with names are usually examples of what are called *l-values*. These include variables and constants, things with a name and a memory location of some sort.

Objectes without names are usually examples of what are called *r-values*. These include results of expressions.

### l-value and r-values

l-value and r-value are what are called *value categories*.

A very rudimentary explanation of what an l-value and r-value is, is that only an l-value can appear on the left-hand-side of an assignment expression, and an r-value usually only appears on the right-hand-side of an assignment expression. 

However, there are so many exceptions to this simple rule now that these are no longer used as the definition - and indeed the terms are further categorised into *pr-value*, *gl-value*, and *xvalue* - but I still find the left-hand-side and right-hand-side rule of thumb as a useful starting point to remember which one is which.

Don't worry too much about fully understanding l-values and r-values just yet, there's plenty of professional C++ engineers who don't understand them, and it is very rare indeed to find one that understands them completely.

## *types*

Another fundamental idea in C++ is the *type*. Any "thing" in C++ has a type, although this applies to more kinds of "things" than "object" does. However, all objects do have a type.

The type is the "kind" of "thing" that a "thing" is. This will probably make more sense with examples, some types are

* `int`, for integer, e.g. `3` is an integer *literal*
* `char`, for character, e.g. `'c'` is a character literal
* `double`, for double precision floating point number, C++'s most commonly used way to represent the real numbers, e.g. `2.3` is a double literal.

There's many many many types available, and much of the work of a C++ engineer is making new types that suit your usage needs, by combining other types together and sometimes adding behaviours to them.

## Example 1

```cpp
#include <iostream>

int main()
{
    int three = 3;

    std::cout << three << '\n';
}
```

In example 1 above, we have two named objects: `three` and `std::cout`, as well as one unnamed object, the literal `\n`. Just by the way, the named objects are l-values and the literal is an r-value.

## Variables

The object named `three` is also called a *variable*. A variable is an object whose value can be changed. In this example, we do not change it, we only *initialise* it, which means it begins life with the intended value already stored in it.

Variables usually have a memory location associated with them - this is basically a box to store the object in, and the variable name is the label on the box.

## Assignment expressions

If a variable is a box to put things in, an assignment expression is how you put something in the box, and usually takes the form of *l-value expression* `=` *r-value expression*.

## Initialisation

In example 1, the assignment expression is `three = 3`, and forms the *direct initialisation* of the variable called `three`. This just means that the box named `three` is created with nothing inside it and then `3` is put in immediately - there's no way to access the empty box.

Variables can also be initialised later - the initialisation is simply the first assignment expression that assigns a value to a variable.

## Example 2

```cpp
#include <iostream>

int main()
{
    int notThreeYet;

    notThreeYet = 3;

    std::cout << notThreeYet << '\n';
}
```

In example 2, we create a variable called `notThreeYet`, but we don't initialise it.

On the following line, we set the value of `notThreeYet` to `3` using an assignment expression.

### Example 2 Questions

1. what would happen if we removed the assignment expression?

Note that uninitialised variables tend to only be an issue with the built-in types, which is a result of

* the C++ committee's choice to continue being compatible with C - (almost) any valid C program is also a valid C++ program
* C and C++'s backward compatibility - (almost) any existing valid C or C++ code should continue to compile and behave as expected with any future version.
* C's history - earlier versions of C didn't allow declarations part way through functions, so they needed a way to declare variables at the top of the function without giving it a value yet, because that would just waste time when it gets overwritten later.

Later, we will have techniques that allow us to avoid these issues without even incurring unnecessary performance hits.

## Example 3

```cpp
#include <iostream>

int main()
{
    int threePointFive = 3.5;

    std::cout << threePointFive << '\n';
}
```

In example two, we use an *assignment expression* try to set the value of `threePointFive`, which is an `int`, to the value of `3.5` which is a `double` literal.

### Example 3 Questions

1. When you build this example, do you see any errors or warnings?

1. What happens when you run it?

1. Can you fix it so that the value printed to the screen is `3.5`?

## Example 4

```cpp
#include <iostream>

int main()
{
    int threeThenFour = 3;

    threeThenFour = 4;

    std::cout << threeThenFour << '\n';
}
```

This program uses an assignment expression outside of the *initialisation* of the variable


### Example 4 Questions

1. What do you think will be printed out by this program?