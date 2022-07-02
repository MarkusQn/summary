# Exceptions

- throwing an exception
    - throw with `throw parameter;`
    - parameter is passed as an argument to the exception handler
    - in a `catch` block just `throw;` for propagating the exception further
- handling exception
    - `try`-`catch` block for handling exception (like in java)
    - exception handler declared with the `catch` keyword
    - syntax for `catch` similar to a regular function with one parameter: `catch (parameter-type parameter-name) {...}`
    - Multiple `catch` expressions possible with different parameter type
    - `catch` block is executed if its parameter-type matches the type of the argument of the `throw` expression
    - If parameter type is reference to class (`&`) it also catches subclasses of that class
    - ellipsis (`...`) is used as the parameter of `catch`, that handler any exception
    - After handling exception, execution resumes after the `try`-`catch` block

Example with elipsis
```c++
try {
  // code here
}
catch (int param) { cout << "int exception"; }
catch (char param) { cout << "char exception"; }
catch (...) { cout << "default exception"; }
```

## exception specification (deprecated !)
- a function declaration can specify the thrown exception with `throw` after parameter list:
```c++
    double myfunction (char param) throw (int);
```
- if function throws a not specified exception: `std::unexpected` is called instead of looking for a handler
- if function specifies `throw()` (empty list): `std::unexpected` is called for any exception
- if no `throw` specification:  `std::unexpected` is never call

# Standard exceptions
- `std::exception` in header `<exception>` is designed to use as base class for objects to be thrown as exceptions
- member function `virtual const char* what() const` to be overwritten to provide description of the exception
- The following subclasses of `std::exception` also defined in header `<exception>` can be used as base classes for custom exceptions:

    | exception       | description                                        |
    | --------------- | -------------------------------------------------- |
    | `logic_error`   | error related to the internal logic of the program |
    | `runtime_error` | error detected during runtime                      |

- All exceptions thrown by components of the C++ Standard library throw exceptions derived from this `exception` class.

    | exception           | description                                             |
    | ------------------- | ------------------------------------------------------- |
    | `bad_alloc`         | thrown by new on allocation failure                     |
    | `bad_cast`          | thrown by dynamic_cast when it fails in a dynamic cast  |
    | `bad_exception`     | thrown by certain dynamic exception specifiers          |
    | `bad_typeid`        | thrown by typeid                                        |
    | `bad_function_call` | thrown by empty function objects                        |
    | `bad_weak_ptr`      | thrown by shared_ptr when passed a bad weak_ptr         |

- Typicall example: checking after exceptin if `new` called

```c++
#include <iostream>
#include <exception>
using namespace std;

int main () {
  try
  {
    int* myarray= new int[1000];
  }
  catch (exception& e)
  {
    cout << "Standard exception: " << e.what() << endl;
  }
  return 0;
}
```

