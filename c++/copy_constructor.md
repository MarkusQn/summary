# Copy constructor
[c++ reference](https://en.cppreference.com/w/cpp/language/copy_constructor)

- A constructor whose first parameter is `T&` (possibly qualified with `const` and/or `volatile`) and
    - there are no other parameters or
    - the rest of the parameters all have default values
```C++
MyClass::MyClass (const MyClass&);
```
- If explicit copy nor move constructors (or assignments) defined, an implicit copy constructor is provided.
- Implicit copy constructor performs a shallow copy of its own members
- called when an object is initialized from another object of the same type, unless overload resolution selects a better match (e.g. Move constructor) or the call is elided. including
    - initialization: `T a = b;` or `T a(b);`, where b is of type T;
    - function argument passing: `f(a);`, where a is of type T and f is `void f(T t);`
    - function return: `return a;` inside a function such as `T f()`, where a is of type T, which has no move constructor.
