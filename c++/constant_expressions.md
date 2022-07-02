# Constant expressions

## Typed constant expressions

- Syntax:
```C++
const <type> <identifier> = <value>;
```
- give a name to a constant value

## constexpr
- Syntax:
```C++
constexpr <type> <identifier> = <value>;
```

- Evaluated by the compiler at compile time
- if it is not initialized by a constant expression, results in a compile error.
- cannot be changed
- function can also be declared constexpr, can than be called inside of constant expression
```C++
constexpr int uses_local_variable() {
  int i = 3;
  return i * 3;
}

constexpr int nine = uses_local_variable();
```

- constexpr variables are implicitly const
- constexpr member functions are not implicit const, but can be eplicitly declared `const`.
- If a class type has a `constexpr` constructor and a trivial destructor, then the class is known as a **literal type**, and it can have `constexpr` member functions

## Preprocessor definitions (#define)

- Syntax:
```C++
#define <identifier> <replacement>
```

- After this directive, any occurrence of identifier is replaced by replacement
- replacement is any sequence of characters (until the end of the line)
- done by the preprocessor
- no semicolone needed after directive