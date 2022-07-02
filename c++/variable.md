# Variables

## Declaration

- Syntax:
```C++
Type Identifier;
```
- `Identifier` can also be multiple names
- Valid identifier: letters, digits (not at beginning), or underscore characters (_)
- variable declaration do NOT need to be at the beginning of a block

Example:
```c++
int a;
int a, b, c;
```

## Initialization of variables
- Initialize variables: variable has a specific value from the moment it is declared
- Three ways to initialize variables (All three ways are equivalent):
```C++
Type Identifier = InitialValue;  // c-like initialization
Type Identifier (InitialValue);  // constructor initialization (C++)
Type Identifier {InitialValue};  // uniform initialization (C++ 2011)
```
- Example:
```C++
int x = 0;
int x (0);
int x {0};
```
- Variables that are not explicitly initialized
    - with *static storage* (global or namespace [[scope]]) are automatically initialized to zeroes
    - with *automatic storage* (block [[scope]]) are left uninitialized, and thus have an undetermined value.

