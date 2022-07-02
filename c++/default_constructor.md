# Default constructor
[c++ reference](https://en.cppreference.com/w/cpp/language/default_constructor)

- a constructor which can be called with no arguments defined with
    - an empty parameter list, or
    - default arguments provided for every parameter
- A type with a public default constructor is DefaultConstructible
- Implicite provided as long as no explicitly declared constructor present in a class.
- A default constructor must be explicitely defined if it is required and it is not implicit defined
- Calling default constructor:

    | Case                                                              | Example                                                               |
    | ----------------------------------------------------------------- | --------------------------------------------------------------------- |
    | is called when an object is declared but no constructor specified | `Rectangle rectb;`<br> `Rectangle[5] rectb; // called for each entry` |
    | It can NOT be called in *functional form*                         | `Rectangle rectb(); // DOES NOT WORK`                                 |
    | It can be called by using *uniform initialization*                | `Rectangle rectb{};`                                                  |
