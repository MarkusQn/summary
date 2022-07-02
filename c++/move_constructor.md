# Move constructor
[c++ reference](https://en.cppreference.com/w/cpp/language/move_constructor)

- A constructor whose first parameter is `T&&` (possibly qualified with `const` and/or `volatile`) and 
    - there are no other parameters or
    - the rest of the parameters all have default values
- Move: the source loses its content, which is taken over by the destination.
- The move constructor is called when an object is initialized (by direct-initialization or copy-initialization) from xvalue or prvalue of the same type, including
    - initialization: `T a = std::move(b);` or `T a(std::move(b));`, where b is of type T;
    - function argument passing: `f(std::move(a));`, where a is of type T and f is `void f(T t);`
    - function return: `return a;` inside a function such as `T f()`, where a is of type T
- When the initializer is a prvalue, the move constructor call is (until C++17 often / since C++17 always) optimized out
