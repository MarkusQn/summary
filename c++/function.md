# Functions
[c++ reference](https://en.cppreference.com/w/cpp/language/function)

## Definition
- Syntax:
```C++
ReturnType Identifier ( ParameterList ) { Statements }
```

- `ReturnType` type of the value returned by the function or `void` if no value returned
- `Identifier` name by which the function can be called.
- `ParameterList`
    - comma seperater list of parameters
    - each parameter consists of a type followed by an identifier
    - if no parameter either `()` or `(void)` 

## Declaration
- A function can only be called if it is *declared* (before in the source file)
- The prototype of a function can be *declared* without actually defining the function completely.
- The declaration shall include all types involved, but the body is replaced by a `;`
- The parameter names are optional
- Examples:
```C++
int protofunction (int first, int second);
int protofunction (int, int);
```

## The return value of main
- return type of main is int
- return statement is optional, if missing implicit `return 0;` at the end
- value 0 or `EXIT_SUCCESS` from header `<cstdlib>` indicate success
- `EXIT_FAILURE` from header `<cstdlib>` indicate failure.

## Arguments passed by value and by reference
- by default parameters are passed *by value*: values are copied (copy constructor is called), changes are not given back
- to pass *by reference*, a [[reference]] can be passed
- Example:
```C++
void swap (int& a, int& b)
{
  int x;
  x = a;
  a = b;
  b = x;
}
```

## const parameter
- for efficiency it can make sense to pass by reference
- if should be read only in the function, add `const` before parameter type
- Example:
```C++
string concatenate (const string& a, const string& b)
{
  return a+b;
}
```

## return passed by value and by reference
- same as with arguments, by default copied back (copy constructor called)
- to pass by *by reference*, a [[reference]] can be returned (it returns a implicit pointer)
    - DON'T return a local variable of the function (it will be ereased)
    - DON'T return reference to a memory location that was allocated in the function

## Default values in parameters
- possible to have optional parameters by providing default value
- Example:
```C++
int divide (int a, int b=2) {..}
```

## Inline functions
- `inline` before function is a hint to the compiler for inlining the function
- Example:
```C++
inline string concatenate (const string& a, const string& b)
{
  return a+b;
}
```

## Overloaded functions
-  two different functions can have the same name if
    - they have a different number of parameters, or
    - any of their parameters are of a different type
- function cannot be overloaded only by its return type