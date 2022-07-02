# Dynamic Memory

## <a name="new"></a> Operators new and new[]
- Syntax:
```C++
pointer = new type
pointer = new type [number_of_elements]
```
- returns a pointer to the beginning of the new block of memory allocated
- `number_of_elements` can be a variable
- two ways to handle that memory allocation failed
    - Default: excsptin `bad_alloc` is thrown
    - nothrow: by adding `nothrow`, a null pointer is returned, example `foo = new (nothrow) int [5];`

## Operators delete and delete[]
- Syntax:
```C++
delete pointer;
delete[] pointer;
```
- releases the memory
- `pointer`can be a *null pointer*, which produces no effect

## Dynamic memory in C
- Also possible to use C-style functions `malloc`, `calloc`, `realloc` and `free`, defined in the header `<cstdlib>`
- Memory blocks allocated by these functions are not necessarily compatible with those returned by `new`, so don't mix