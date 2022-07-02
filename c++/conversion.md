# Conversion

## Implicit conversion
- *standard conversion*: conversion without need of any explicit operator, allows the conversions
    - between numerical types (short to int, int to float, double to int...) to or from bool
        - *promotion*
            - conversion from samaller type, produces the exact same value in the destination type
        - *numeric conversions*
            - unlike the promotions, may changes the values, with potential loss of precision.
            - with compiler option `-Wconversion` generates warning
    - some pointer conversions
        - Null pointers -> pointers of any type
        - Pointers to any type -> void pointers
        - Pointer *upcast*: pointers to derived class -> pointer to base class

## conversions with classes
Implicit conversions provided by three members of a class:

- Single-argument constructors: from a particular type (initialize an object)
    - Syntax: `<Class Name> (const <Source Type>& x) {...}`
- Assignment operator: from a particular type (on assignments)
    - Syntax: `<Class Name>& operator=(const <Source Type>& x) {...}`
- Type-cast operator: to a particular type.
    - Syntax: `operator <Target Type>() {...}` (Note: no return type)

Example:
```C++
// implicit conversion of classes:
#include <iostream>
using namespace std;

class A {};

class B {
public:
  // conversion from A (constructor):
  B (const A& x) {}
  // conversion from A (assignment):
  B& operator= (const A& x) {return *this;}
  // conversion to A (type-cast operator)
  operator A() {return A();}
};

int main ()
{
  A foo;
  B bar = foo;    // calls constructor
  bar = foo;      // calls assignment
  foo = bar;      // calls type-cast operator
  return 0;
}
```

- `explicit` keyword
    - Single-argument constructors
        - explicite constructor call required for function call `fn(B(a))` (a: val of source type, B target type)
        - Variable initialization syntax on declaration not allowed `B b = a;`
    - Type-cast operator: explicite call required for:
        - on function call `fn(b.operator A())`
        - on assignment `a = b.operator A();`

## Type casting
Overview for class pointers:

|                                                   | upcast | same | downcast obj valid target type | downcast obj NOT valid target type | incompatible type  |
| ------------------------------------------------- | ------ | ---- | ------------------------------ | ---------------------------------- | ------------------ |
| implicite conversion `b = a;`                     |  OK    | OK   | compile time error             | compile time error                 | compile time error |
| `b = dynamic_cast <B*> (a);` a is NOT polymorphic |  OK    | OK   | compile time error             | compile time error                 | compile time error |
| `b = dynamic_cast <B*> (a);` a is polymorphic     |  OK    | OK   | OK                             | NULL                               | NULL               |
| `b = static_cast <B*> (a);`                       |  OK    | OK   | OK                             | OK                                 | compile time error |
| explicite conversion `b = (B*)a;`                 |  OK    | OK   | OK                             | OK                                 | OK                 |
| `b = reinterpret_cast <B*> (a);`                  |  OK    | OK   | OK                             | OK                                 | OK                 |

- explicit conversion
- two syntaxes
    - *functional*, example: `y = int (x); `
    - *c-like*, example: `y = (int) x;`
- allows to convert any (class) pointer into any other (class) pointer type, dangerous!!
- to control conversions between classes, four specific casting operators:
    - `dynamic_cast <new_type> (expression)`
        - used with pointers and references to classes (or with void*)
        - includes conversion:
            - *upcast*: pointers to derived class -> pointer to base class
            - *downcast* pointers to base class -> pointer to derived class for polymorphic classes (those with virtual members) if and only if the pointed object is a valid complete object of the target type.
            - Null pointers -> pointers of any type
            - Pointers to any type -> void pointers
        - If conversion not possible:
            - with pointers: return `null`
            - with reference: throws `bad_cast` exception
    - `static_cast <new_type> (expression)`
        - used width pointers to classes
        - includes conversion:
            - *upcast*: pointers to derived class -> pointer to base class
            - *downcast* pointers to base class -> pointer to derived class, width no check
            - Null pointers -> pointers of any type
            - Pointers to any type -> void pointers
            - Convert integers, floating-point values and enum types to enum types
    - `reinterpret_cast <new_type> (expression)`
        - converts any pointer type to any other pointer type, even of unrelated classes
        - It can also cast pointers to or from integer types
    - `const_cast <new_type> (expression)`
        -  manipulates the constness of the object pointed by a pointer, either to be set or to be removed.

## typeid
- Syntax
```c++
typeid (expression)
```

- returns a reference to constant object of type `type_info`, defined in header `<typeinfo>`
- values can be compared with `==` and `!=`
- `typeid(pointer)` is the pointer type itself
- `typeid(*pointer)` if pointed to a class returns the dynamic type
- `.name()` returns a **compiler dependent** string representation
