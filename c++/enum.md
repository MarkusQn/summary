# Enumerated types (enum)

- Syntax:
```C++
enum type_name {
  value1,
  value2,
  value3,
  .
} object_names;
```
- creates the type type_name, which can take any of value1, value2, value3, ... as value.
- Values are implicitly convertible to an integer type.
    - Enum are always assigned an integer numerical equivalent internally
    - By default the value starts by 0 and are continous numbered
    - A value can be specified for any of the possible values
        - if only some value provided: automatically continued with numbering
```C++
enum months_t { january=1, february, march, april,
                may, june, july, august,
                september, october, november, december} y2k;
```

## Enumerated types with enum class
- `enum class` or `enum struct` creates an enum that is not implicitly convertible to int
- Gives type safety
- Values need to be accessed width scope
- Example:
```C++
enum class Colors {black, blue, green, cyan, red, purple, yellow, white};

Colors mycolor = Colors::blue;
```
- underlying type can be specified, such as `char`, `short`, `unsigned int`.
```C++
enum class EyeColor : char {blue, green, brown}; 
```