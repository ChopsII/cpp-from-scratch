# Function Declaration

## Purpose

Tells the compiler that there will be a function with a given name, return value, parameters, and cv and reference modifiers

## Basic form

The basic function declaration takes the form:

```cpp
ReturnType functionName();
```

where:

* `ReturnType` names a [type]() that the [function]() will return
* `functionName` names the [function]() itself, so that you can refer to it and call it

## Variations

### With parameters

```cpp
ReturnType functionName(Parameter1Type parameter1Name, Parameter2Type parameter2Name);
```

* While example has only 2 parameters, any number of parameters can be added inside the parentheses, separated by commas. 
* `Parameter1Type` names the [type]() of the first [parameter](), which means that when you [call the function](function_call.md), you will need to provide an [argument]() of the same or compatible [type]()

### Trailing return type

```cpp
auto functionName() -> ReturnType;
```

* This is functionally exactly the same as the basic function declaration, it is just a style preference
* Some more advanced techniques using [function templates]() sometimes benefit from this form

### Declaration and Definition in one

```cpp
ReturnType functionName() {}
```

* If a [function definition]() doesn't match any existing function declaration, it will implicitly be a function declaration itself

> Tip: to avoid this happening accidentally, i.e. you are intending to define an existing declaration, fully qualify your functionName. This disallows the implicit declaration, forcing the compiler to raise a compiler error if the [signature] doesn't match a prior declaration.

## Unusual, superseded, or otherwise not-recommended variations

### With unnamed parameters (not generally recommended)

```cpp
ReturnType functionName(Parameter1Type, Parameter2Type);
```

* Parameters in a function declaration do not need to be named; only their types must be named. However, naming the parameters can help convey the purpose of each parameter to a consumer of the function
* Even if the parameters are named, the parameter names do not have to match the [function definition]()'s parameter names.

### C-style variadic function (recommended to avoid where possible)

```cpp
ReturnType functionName(Parameter1Type parameter1Name, ...);
```

* This is the C way to allow any number of arguments - of any types - to be passed to the function
* Not type safe
* Prefer using a [variadic function template]() instead