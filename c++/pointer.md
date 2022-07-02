# Pointers

## Operator \* and &
- *Address-of operator* (&)
    - Returns the address (a pointer) of a variable
    - Can be read as "address of"
    - Syntax: `&variable`
    - Example: `fooPtr = &fooVar;`
- *Dereference operator* (\*)
    - Returns the value stored at address (of that pointer)
    - Can be read as "value pointed to by".
    - Syntax: `*pointer`
    - Example: `fooVar = *fooPtr`

## Declaring pointers
- Syntax:
```C++
Type * Identifier;
```
- type is the data type pointed to by the pointer
- like other variable, multiple `* Identifier` possible
- the asterisk (\*) used means that it is a pointer and is NOT the *Dereference operator*
- Example:
```c++
int * number;
char * p1, * p2;
```
- Pointers to pointers possible: `char ** c;`

## Initializing pointers
- Pointers can be initialized to point to specific locations at the very moment they are defined:
```C++
int myvar;
int * myptr = &myvar;
```

## Pointers and arrays
- Arrays work like pointers to their first elements
- Array can always be implicitly converted to the pointer of the corresponding type
- Pointers and arrays support the same set of operations, with the same meaning for both.
- The main difference between pointers and arrays is:
    - pointers can be assigned a different address
    - arrays can never be assigned anything, and will always represent the same block of elements
- The brackets (`[]`) are a dereferencing operator known as *offset operator*. They dereference the variable they just as * does
- The following expressions are equivalent, `a` can be a pointer as well as an array:
```C++
a[5] = 0;
*(a+5) = 0;
```

## Pointer arithmetics
- only addition and subtraction operations are allowed
- the addition / subtraction are on (array) position of the type to that is pointed
    - added / subtracted value is multiplied by the type size
- The expression `*p++` is the same as `*(p++)`

## Pointers and const
- If type pointed to by the pointer is qualified as `const`, the value pointed to can be read but not modified.
- A pointer to non-const can be implicitly converted to a pointer to const, but not the other way around!
```C++
int y = 10;
const int * p = &y;
*p = x;             // Compile time ERROR
```
- The `const` qualifier can either precede or follow the pointed type, with the exact same meaning:
```C++
const int * p2a = &x;
int const * p2b = &x;
```
- One use case of pointers to const is as function parameter
- The pointers itself can still be incremented or assigned different addresses
```C++
void print_all (const int* start, const int* stop)
{
  const int * current = start;
  while (current != stop) {
    cout << *current << '\n';
    ++current;     // increment pointer
  }
}
```
- Pointers can also be themselves const: append `const` to the pointed type (after the asterisk):
```C++
int x;
      int *       p1 = &x;  // non-const pointer to non-const int
const int *       p2 = &x;  // non-const pointer to const int
      int * const p3 = &x;  // const pointer to non-const int
const int * const p4 = &x;  // const pointer to const int
```

## void pointers
- void pointers are are able to point to any data type
- the data pointed to by a void pointer cannot be directly dereferenced
    - needs first be transformed into some other pointer type that points to a concrete data type before being dereferenced.

## Invalid pointers
- Pointers can actually point to any address, including addresses that do not refer to any valid element
- Typical examples:
    - uninitialized pointers
    - pointers to nonexistent elements of an array
- Accessing such a pointer causes undefined behavior

## null pointers
- explicitly point to nowhere: null pointer
- expressed in C++ in following ways:
    - integer value of `0`
    - the `nullptr` keyword
    - defined constant `NULL`
-  all null pointers compare equal to other null pointers

## Pointers to functions
- Typical use case: passing a function as an argument to another function.
- Declaration: Same as a regular function declaration, except 
    - the parameter/variable name of the function pointer is at the position of the function name
    - the name has an asterisk (\*) before and is enclosed between parentheses () `(*<name>)`
- Example:

```C++
int subtraction (int a, int b)
{ return (a-b); }

int main ()
{
  // Declare variable or function parameter (with name funcptr)
  int (*funcptr)(int,int);

  // get pointer to function
  funcptr = subtraction;

  // call function of functionptr
  int r = (*funcptr)(5,2);
}
```
