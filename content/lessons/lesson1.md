# Lesson 1: 'Hello World!'

It has become a tradition of sorts to begin any course teaching a programming language to begin with the example of writing a small program to write "Hello, World!" to the screen.

This is what such a program looks like in C++:

## Example 1.1

```cpp
#include <iostream>

int main()
{
    std::cout << "Hello, World!\n";
}
```

Try it for yourself! Go to <https://repl.it/languages/cpp> (or any online C++ IDE of choice) and carefully type in the source code of the program above, and click run.

Feel free to play around with it a little.

Some things you might like to explore:

### Ex 1.1 Questions

* What happens if you leave off the `\n`?
* What about the `;`?
* Can you change the [whitespace](../terms/whitespace.md) without causing the behaviour to change?
* Can you understand the [errors](../terms/error.md) that show when you don't type it out exactly? Try making some errors on purpose by adding or removing characters in various place

## Breakdown of the code

Now, we're going to go through the code bit-by-bit and explain what each part means.

There's quite a lot to get through here and you're not going to understand much of it at first! I just want to expose you to the ideas and terms and give you a reference to look back on.

The real understanding will come with practice - I often liken learning to program like bashing your head on the desk until the computer does what you want. It usually feels completely useless but, eventually, it will just click.
Practising is the only thing that you can do to make it more likely to happen or happen any sooner. So, practise!

Now, back to the breakdown

### Line 1

```cpp
#include <iostream>
```

#### [Preprocessor Directive](../terms/preprocessor_directive.md)

The first character on the line, `#`, indicates that this line is what is called a [Preprocessor Directive](../terms/preprocessor_directive.md) - it "directs" the [preprocessor](../terms/preprocessor.md) to do something in particular. The preprocessor is a tool that runs as the first step of [building](../terms/building.md) a C++ [program](../terms/program.md). The preprocessor is like a very simple language of its own, and has a few directives that are useful to know.

#### Include directive

This particular preprocessor directive is an [include directive](../terms/include_directive.md) - sometimes called a hash-include - which tells the preprocessor to go away and find a file called `iostream` (it comes with any compliant compiler), preprocess it, and paste the result into this source in place of this line. That is, the [compiler](../terms/compiler.md) itself never actually sees this preprocessor directive, instead, in place of this line, it sees the source of the file called `iostream` - after it has been preprocessed.

#### Angle brackets versus quotes in Include Directive

>note: This isn't necessary to understand the example; it is letting you know that there's an alternate form which you will likely see often.

An alternative way to write the include directive is `#include "iostream"`. The difference is the quotes (`"` and `"`) around the file to include, as opposed to the angle brackets (`<` and `>`) in the original. The two forms are very similar, but they do have a slight difference in meaning; the form with quotes is allowed to first search for the file to be included in the same location as the file that the directive appears in, before searching the [include paths](../terms/include_paths.md). The angle brackets form is only allowed to search for the file in the include paths.

For example, if, in Example 1.1, we had `#include "iostream"` instead, it would still work. However, if we happened to also have a file in the same directory as our source file called `iostream`, then that file would be included _instead_ of the standard one.

#### iostream

The `iostream` file is a [header file](../terms/header-file.md) from the [standard library](../terms/standard_library.md). We include this file so that we have access to some useful things that are [defined](../terms/defined.md) in it, in this case the `std::out` [stream](../terms/stream.md) [object](../terms/object.md), which allows us to write characters to the [terminal](../terms/terminal.md), as well as the [operator<<](../terms/operator<<.md) functions that we use to specify what things we want to write to that stream object.

### Line 2

This line is left blank purely for readability. It is useful to use blank lines to separate conceptually or mentally separate parts of the source file, however this is entirely up to the preference of the programmer or the team of programmers, as the case may be. C++ is generally [whitespace](../terms/whitespace.md) [agnostic](../terms/agnostic.md) - it doesn't care how many spaces, tabs, or newlines you use in your code, so long as there's at least one in each place where it is needed.

### Line 3

```cpp
int main()
```

#### Function declaration

In this location in the code (or, at this [scope](../terms/scope.md)), the pattern of [symbol](../terms/symbol.md)-[whitespace](../terms/whitespace.md)-symbol-parentheses (as in `int main()`) means that this line is a [function declaration](../terms/function-declaration.md). There are [keywords](../terms/keywords.md) that can also appear in this pattern which modify some properties about the function, but we don't need any in this example, and, in fact, if we used any, the [program](../terms/program.md) likely wouldn't run, as the [main function](../terms/main-function.md) has to match a certain [signature](../terms/function-signature.md) to be valid and to be found by the [build system](../terms/build-system.md) to tell the program where its [entry point](../terms/entry-point.md) is.

#### The most vexing parse

>note: this is not necessary to understand in this example, but it is a common enough pitfall that it is good to know about it.

Unfortunately, there are other things that might otherwise use this pattern, namely, [declaring](../terms/declaration.md) a [variable](../terms/variable.md) at [global scope](../terms/global-scope.md) and [default initialising](../terms/default-initialisation.md) it - in this case, the line `int main()` could (erroneously) be thought to be declaring a variable of [type] [int], called `main`, and initialising it with a default value (0 for `int`s).
However, there is a rule that states that 'anything that can be interpreted as a valid function declaration and is in a location where a function declaration would be legal, is a function declaration'. This apparent ambiguity has confused many people, enough that it has a name: the [most vexing parse](../terms/most-vexing-parse.md). Luckily, there are other ways to declare global variables and default initialise them which don't conflict with function declaration [syntax](../terms/syntax.md). We will of course get to these in due time; we don't have any variable declarations in this example.

#### int

[`int`](../terms/`int`.md) is the name given to the [type](../terms/type.md) which represents the integers, at least the most commonly used subset of them. `int` is a [signed type](../terms/signed type.md), which means it can hold negative numbers. `int` can have different [bit width](../terms/bit width.md) on different systems, but most commonly it is a 32 [bit](../terms/bit.md) number, which means it can hold integer values from -2,147,483,648 to 2,147,483,647. It is required to be at least 16 bits wide, and at least as wide as the `char` type.

#### Return type

In this line of code, the `int` type is specifying the [return type](../terms/return-type.md) of the function - that is, when this function completes [execution](../terms/execute.md), it will give the [caller](../terms/caller.md) an `int` value. This lets the caller know that it will need to have a place to put the `int` returned, and also helps the compiler make sure that the programmer [implementing](../terms/implement.md) the `main` function actually remembers to [return](../terms/return.md) an `int` value.

#### built-in types

`int` is a [built-in type](../terms/built-in-type.md), which means it is part of the [language](../terms/language.md). You don't need to include anything to be able to use it, and it is available on all [conforming](../terms/conforming.md) [build systems](../terms/build-system.md). The names of built-in types are also keywords, which means you're not allowed to name anything such that it conflicts with a keyword.

#### Function name

The next part of line 3 after `int` is the [function name](../terms/function-name.md), in this case `main`. This specifies the [symbol](../terms/symbol.md) that may be used to refer to this function in other code. Functions names have to follow similar naming rules to variables, but otherwise can be just about anything. In this case, however, we need to call it `main` because we need to adhere to the [function signature](../terms/function-signature.md) required by the standard and the build system so that it knows that this function is the entry point to our program.

#### Parameter list

After the function name, there is a pair of parentheses (as in `()`). This is used to indicate that the symbol just named `main` is a function, and also specifies the types of the [parameters](../terms/parameters.md) that this function takes. In this case, we take no parameters, so the parentheses are empty. The [main function](../terms/main-function.md) is allowed to take either zero parameters or two parameters of type `int` and `char**`, which can be used to allow a program to take [arguments](../terms/command-line-arguments.md) from the [command line](../terms/command-line.md). We will deal with this other form later.

### Line 4

```cpp
{
```

#### Opening brace

An [opening brace](../terms/braces.md) (aka left squiggly bracket) like this signifies the beginning of a [block](../terms/block.md). This means that everything between this opening brace and the matching closing brace belongs to the construct immediately preceding the opening brace.
The brace can be put on the line above (or on the line below), but my personal preference is to give it a line of its own to clearly distinguish the code above and within the block - especially useful when things like function signatures get overly complicated.

#### Function definition

The block surrounded by braces is, in this case, a [function definition](../terms/function-definition.md).
This is because any block following a function declaration is interpreted as a function definition for that function.
In this case, everything in this block is [executed](../terms/execution.md) when the `main` function is called.

#### Line 5

expressions

statements
