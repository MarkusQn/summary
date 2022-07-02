# char[]
- C-strings are null-terminated char arrays.
- String literals are null-terminated char arrays and not string objects.
- char arrays can be initialized by a string literal.
- The following two declaration result in the same
```c++
char myword[] = { 'H', 'e', 'l', 'l', 'o', '\0' };
char myword[] = "Hello"; 
```
- char arrays can NOT be assigned to each other (like other arrays)


# String

- `string` is a compound type
- All three way of initialization possible

```c++
string mystring = "This is a string";
string mystring ("This is a string");
string mystring {"This is a string"};
```

# Coexistence of char[] and strings
- many function of the standard library are overloaded with `char[]` and `string` version
- There is a implicit conversion from `char[]` to `string`
- `string` has function `c_str` and `data` that both convert `string` to `char[]`.