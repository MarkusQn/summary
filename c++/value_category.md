# Value Category

- *lvalues* and *rvalues* are semantic properties of expressions
- *lvalue* is an expression that yields an object reference, it always has a defined region of storage, so you can take its address. Examples:
    - a variable name
    - an array subscript reference
    - `*p` dereferenced pointer
    - a function call that returns a reference
- *rvalue* is an expression that’s not an *lvalue*.
    - represent modifiable objects that are no longer needed
    - Examples:
        - literal
        - a function call whose return type is non-reference
        - aritmetic and logical expression
        - `&a` address-of expression
        - `this` pointer
- *non-modifiable lvalue*: if an lvalue has a const-qualified type.


The following table:

|                       | can take the address of | can assign to |
| --------------------- | ----------------------- | ------------- |
| lvalue                | yes                     | yes           |
| non-modifiable lvalue | yes                     | no            |
| (non-class) rvalue    | no                      | no            |