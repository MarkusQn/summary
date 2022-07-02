# Arrays

## Definition
- Syntax
```C++
Type Identifier [Elements];
```
- `Type` is a valid type (such as int, float...)
- `Ìdentifier` is the name
- `Elements` specifies the length of the array, must be a *constant expression*
- Note: `Elements` after identifier and NOT after type as normally done in Java
- Example:
```C++
int foo [5];
```

## Initializing arrays
- Syntax
```C++
Type Identifier [Elements] = { InitialValues };
```
- Example:
```C++
int foo [5] = { 16, 2, 77, 40, 12071 }; 
```
- The number of InitialValues shall not be greater than `Elements`.
- If the number of InitialValues is smaller than `Elements`, then the remaining elements are set to the default value (e.g. 0).
- InitialValues can also be empty, which initialzes all values to the default value (e.g. 0). Example:
```C++
int foo [5] = { }; 
```
- If `Elements` is left away (empty `[]`), the compiler will assume automatically a size for the array that matches the number of `InitialValues`. Example:
```C++
int foo [] = { 16, 2, 77, 40, 12071 };
```
- With *universal initialization*, the `=` can be left away. Example:
```C++
int foo[] { 16, 2, 77, 40, 12071 };
```
- Like other variables, arrays with *static storage* (global or namespace [scope](scope.md)) are default-initialized if not explicit initialized.

## Accessing the values of an array
- Syntax
```C++
name[index]
```
- `Index` is zero based
- No bound check, therefore possible to access outside the storage of that array

## Multidimensional arrays
- Arrays of arrays
- multidimensional arrays are just an abstraction for programmers, since the same results can be achieved with a simple array, by multiplying its indices:
```C++
int jimmy [HEIGHT][WIDTH];
jimmy[n][m] = 2;

// is same as :

int jimmy [HEIGHT * WIDTH];
jimmy[n*WIDTH+m] = 2;
```

## Arrays as parameters
- Parameter definition does contain empty brackets, e.g. `void f (int arg[])`
- Width multidimensional arrays only the first dimension can be empty: e.g. `void f (int arg[][3][4])`
- Arrays are passed by reference.

## Array copy / assignment
- it is NOT possible to assign a array to another array, only single elements
```C++
int a[3] = {5,6,7};
int b[3] = {};
b = a;            // COMPILE TIME ERROR
```
- Use C style `memcpy` or C++ style `std::copy`

## Library arrays
- C++ provides an alternative: a standard container type called `array`
- It is a type template defined in header <array>
- it also knows its size and supports deep copy.