# Special member functions
- member functions that are implicitly defined as member of classes under certain circumstances

| Member function                               | typical form for class a C  | implicitly defined ("no" = not user-declared):                                                   | default definition: |
| --------------------------------------------- | --------------------------- | ------------------------------------------------------------------------------------------------ | ------------------- |
| [default constructor](default_constructor.md) | `C::C();`                   | if no other constructors                                                                         | does nothing        |
| [destructor](destructor.md)                   | `C::~C();`                  | if no destructor                                                                                 | does nothing        |
| [copy constructor](copy_constructor.md)       | `C::C (const C&);`          | if no [move constructor](move_constructor.md) and no [move assignment](move assignment.md)                                            | copies all members  |
| [copy assignment](copy_assignment.md)         | `C& operator= (const C&);`  | if no [move constructor](move_constructor.md) and no [move assignment](move_assignment.md)                                            | copies all members  |
| [move constructor](move_constructor.md)       | `C::C (C&&);`               | if no [destructor](destructor.md), no [copy constructor](copy_constructor.md), no [copy assignment](copy_assignment.md) and no [move assignment](move_assignment.md) | moves all members   |
| [move assignment](move_assignment.md)         | `C& operator= (C&&);`       | if no [destructor](destructor.md), no [copy constructor](copy_constructor.md), no [copy assignment](copy_assignment.md) and no [move constructor](move_constructor.md)| moves all members   |

- It can be selected explicitly which of these members exist with their default definition or which are deleted by using the keywords `default` and `delete`, respectively.
- The syntax is either one of:
```C++
function_declaration = default;
function_declaration = delete;
```
- `=default` and `=deleted` also count as *user-declared* 
- Some types provide only a [move constructor](move_constructor.md) and [move assignment](move_assignment.md), but not a [copy constructor](copy_constructor.md) or [copy assignment](copy_assignment.md); such objects can only be moved, not copied (example `std::unique_ptr`)
- A move operation leaves the source object in a "valid but unspecified" state
- The move operations can be forced with `std::move()`
    - Example: `std::unique_ptr<Foo> foo2 = std::move(foo1);`
    - Some rules of thumb for using `std::move()`
        - Use `std::move()` if your code won't compile without it
        - Consider using `std::move` to permit a move instead of a copy on the last use of a variable (if efficient move)
        - Do **not** use `std::move()` when the copy you're trying to optimize would have been using [copy elision](copy elision.md)
        - Don't trust objects after you've called `std::move()` on them.

Some rules:

- *rule of zero*: If you can avoid explicitly defining special member functions, do.
- *rule of three*: If a class requires a user-defined [destructor](destructor.md), a user-defined [copy constructor](copy_constructor.md), or a user-defined [copy assignment](copy_assignment.md) operator, it almost certainly requires all three.
- *rule of five*:  a user-declared [destructor](destructor.md), [copy constructor](copy_constructor.md), or [copy assignment](copy_assignment.md) operator prevents implicit definition of the [move constructor](move_constructor.md) and the [move assignment](move_assignment.md) operator, any class for which move semantics are desirable, has to declare all five special member functions
