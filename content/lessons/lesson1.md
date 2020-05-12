# Lesson 1: 'Hello World!'

It has become a tradition of sorts to begin any course teaching a programming language to begin with the example of writing a small program to write "Hello, World!" to the screen.

This is what such a program looks like in C++:

```cpp
#include <iostream>

int main()
{
    std::cout << "Hello, World!\n";
}
```

Try it for yourself! Go to <http://cpp.sh> (or any online C++ IDE of choice) and carefully type in the source code of the program above, and click run.

Feel free to play around with it a little.

Some things you might like to explore

* What happens if you leave off the `\n`?
* What about the `;`?
* Can you change the whitespace without causing the behaviour to change?
* Can you understand the errors that show when you don't type it out exactly?

## Breakdown of the code

Now, we're going to go through the code bit-by-bit and explain what each part means.

There's quite a lot to get through here and you're not going to understand much of it at first! I just want to expose you to the ideas and terms and give you a reference to look back on. 

The real understanding will come with practice - I often liken learning to program like bashing your head on the desk until the computer does what you want. It usually feels completely useless and like you can't do anything to make it happen any sooner or more certainly, but eventually it will just click - as long as you practice.

### Line 1

```cpp
#include <iostream>
```

#### Preprocessor Directive

The first character on the line, `#`, indicates that this line is what is called a *Preprocessor Directive* - it "directs" the *preprocessor* to do something in particular. The preprocessor is a tool that runs as the first step of *building* a C++ *program*. It is very simple, and has a few directives that are useful to know.

#### Include directive

This particular preprocessor directive is a *#include directive* - sometimes called a hash-include - which tells the preprocessor to go away and find a file called `iostream`, preprocess it, and paste the result into this source in place of this line. That is, the *compiler* itself never actually sees this preprocessor directive, instead it sees the source of the file called iostream after it has been preprocessed.

#### Angle brackets versus quotes in Include Directive

An alternative way to write the include directive is `#include "iostream"`. The difference is the quotes around the file to include, as opposed to the angle brackets in the original. The two forms are very similar, but they do have a slight difference in meaning; the form with quotes is allowed to first search for the file being included in the same location as the file that the directive appears in, before searching the *include paths*. The angle brackets form is only allowed to search for the file in the include paths.

#### iostream

The iostream file is a *header file* from the *standard library*. We include this file so that we have access to some useful things that are *defined* in it, in this case the `std::out` *object*, which allows us to write characters to the terminal, as well as the *operator<<* functions that we use to specify what things we want to write to that *stream*.

### Line 2

This line is left blank purely for readability. It is useful to use blank lines to separate conceptually or mentally separate parts of the source file, however this is entirely up to the preference of the programmer or the team of programmers, as the case may be.

### Line 3

```cpp
int main()
```

#### Function declaration

In this location (or, at this *scope*), the pattern of *symbol*-*whitespace*-symbol-parentheses means that this line is a *function declaration*. There are *keywords* that can also appear in this pattern, but we don't need any in this example.

#### The most vexing parse

Unfortunately, there are other things that might otherwise use this pattern, namely, *declaring* a *variable* at *global scope* and *default initialising* it, but there is a rule that anything that can be interpreted as a function declaration and is in a location where a function declaration would be legal, is a function declaration. This apparent ambiguity has confused many people, enough that it has a name: the *most vexing parse*. Luckily, there are other ways to declare global variables and default initialise them that don't conflict.

#### int

*`int`* is the name given to the *type* which represents the integers, at least the most commonly used subset of them. `int` is a *signed type*, which means it can hold negative numbers. `int` can have different *bit width* on different systems, but most commonly it is a 32 *bit* number, which means it can hold integer values from -2,147,483,648 to 2,147,483,647, and is required to be at least 16 bits wide, and at least as wide as the `char` type.

#### built-in types

`int` is a *built-in type*, which means it is part of the *language*. You don't need to include anything to be able to use it, and it is available on all *conforming* build systems. The names of built-in types are also keywords, which means you're not allowed to name anything such that it conflicts with a keyword.