# Move assignment
[c++ reference](https://en.cppreference.com/w/cpp/language/move_assignment)

- An overload of `operator=` which takes a exactly one parameter of type `T&&` (possibly qualified with `const` and/or `volatile`)
- called whenever it is selected by overload resolution, e.g. when 
    - an object appears on the left-hand side of an assignment expression
    - the right-hand side is an rvalue of the same or implicitly convertible type