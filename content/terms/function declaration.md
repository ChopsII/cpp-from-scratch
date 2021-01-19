# Function Declaration

The basic function declaration takes the form:

```cpp
ReturnType functionName();
```

where:

* `ReturnType` names a [type]() that the [function]() will return
* `functionName` names the [function]() itself, so that you can refer to it and call it

Variations:

## With parameters

```cpp
ReturnType functionName(Parameter1Type parameter1Name, Parameter2Type parameter2Name);
```

* Any number of parameters can be added inside the parentheses, separated by commas
* `Parameter1Type` names the [type]() of the first [parameter](), which means that when you [call the function](function_call.md), you will need to provide an [argument]() of the same or compatible [type]()

## Trailing return type

```cpp
auto functionName() -> ReturnType;
```

## Declaration and Definition in one

```cpp
ReturnType functionName() {}
```

* If a [function definition]() doesn't match any existing function declaration, it will implicitly be a function declaration itself

> Tip: to avoid this happening accidentally, i.e. you are intending to define an existing declaration, fully qualify your functionName. This disallows the implicit declaration, forcing the compiler to raise a compiler error if the [signature] doesn't match a prior declaration.
