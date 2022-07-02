# Special member functions
- member functions that are implicitly defined as member of classes under certain circumstances

| Member function         | typical form for class a C  | implicitly defined ("no" = not user-declared):                                                   | default definition: |
| ----------------------- | --------------------------- | ------------------------------------------------------------------------------------------------ | ------------------- |
| [[default constructor]] | `C::C();`                   | if no other constructors                                                                         | does nothing        |
| [[destructor]]          | `C::~C();`                  | if no destructor                                                                                 | does nothing        |
| [[copy constructor]]    | `C::C (const C&);`          | if no [[move constructor]] and no [[move assignment]]                                            | copies all members  |
| [[copy assignment]]     | `C& operator= (const C&);`  | if no [[move constructor]] and no [[move assignment]]                                            | copies all members  |
| [[move constructor]]    | `C::C (C&&);`               | if no [[destructor]], no [[copy constructor]], no [[copy assignment]] and no [[move assignment]] | moves all members   |
| [[move assignment]]     | `C& operator= (C&&);`       | if no [[destructor]], no [[copy constructor]], no [[copy assignment]] and no [[move constructor]]| moves all members   |

- It can be selected explicitly which of these members exist with their default definition or which are deleted by using the keywords `default` and `delete`, respectively.
- The syntax is either one of:
```C++
function_declaration = default;
function_declaration = delete;
```
- `=default` and `=deleted` also count as *user-declared* 
- Some types provide only a [[move constructor]] and [[move assignment]], but not a [[copy constructor]] or [[copy assignment]]; such objects can only be moved, not copied (example `std::unique_ptr`)
- A move operation leaves the source object in a "valid but unspecified" state
- The move operations can be forced with `std::move()`
    - Example: `std::unique_ptr<Foo> foo2 = std::move(foo1);`
    - Some rules of thumb for using `std::move()`
        - Use `std::move()` if your code won't compile without it
        - Consider using `std::move` to permit a move instead of a copy on the last use of a variable (if efficient move)
        - Do **not** use `std::move()` when the copy you're trying to optimize would have been using [[copy elision]]
        - Don't trust objects after you've called `std::move()` on them.

Some rules:

- *rule of zero*: If you can avoid explicitly defining special member functions, do.
- *rule of three*: If a class requires a user-defined [[destructor]], a user-defined [[copy constructor]], or a user-defined [[copy assignment]] operator, it almost certainly requires all three.
- *rule of five*:  a user-declared [[destructor]], [[copy constructor]], or [[copy assignment]] operator prevents implicit definition of the [[move constructor]] and the [[move assignment]] operator, any class for which move semantics are desirable, has to declare all five special member functions
