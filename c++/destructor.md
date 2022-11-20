# Destructor
[c++ reference](https://en.cppreference.com/w/cpp/language/destructor)

- opposite functionality of constructors
- it takes no arguments, returns nothing and is named `~ClassName`
- The destructor for an object is called at the end of its lifetime

## Destruction sequence
For both user-defined or implicitly-defined destructors

1. execute the body of the destructor and destroying any automatic objects allocated within the body of the destructor (local variables),
1. call the destructors for all non-static non-variant data members of the class (in reverse order of declaration)
1. call the destructors of all direct non-virtual base classes (in reverse order of construction (which in turn call the destructors of their members and their base classes, etc)
1. if this object is of most-derived class, calls the destructors of all virtual bases.

Even when the destructor is called directly (e.g. `obj.~Foo();`), the return statement does not return control to the caller immediately: it calls all those member and base destructors first.