# Operator overloading
- most operators can be overloaded so that their behavior can be defined for just about any type, including classes
- Overloading operators done by regular functions with special names
```C++
type operator sign (parameters) { /*... body ...*/ }
```
Example:
```C++
class CVector {
  public:
    ...
    CVector operator + (const CVector&);
};

CVector operator+ (const CVector& lhs, const CVector& rhs) {
  CVector temp;
  temp.x = lhs.x + rhs.x;
  temp.y = lhs.y + rhs.y;
  return temp;
}
```
- some operators can be overloaded in two forms: either as a member function or as a non-member function
- Operator called either implicitly using the operator, or explicitly using its functional name
```C++
c = a + b;
c = a.operator+ (b);
```

- The following table shows all the oprators
    - replace @ by the operator
    - a is an object of class A, b is an object of class B, c is an object of class C
    - TYPE is just any typ

    | Expression  | Operator                                                                            | Member function         | Non-member function |
    | ----------- | ----------------------------------------------------------------------------------- | ----------------------- | ------------------- |
    | `@a`        | `+` `-` `*`(Dereference) `&`(Address-of) `!` `~` `++` `--`                          | `A::operator@()`        | operator@(A)        |
    | `a@`        | `++` `--`                                                                           | `A::operator@(int)`     | operator@(A,int)    |
    | `a@b`       | `+` `-` `*` `/` `%` `^` `&` `|` `<` `>` `==` `!=` `<=` `>=` `<<` `>>` `&&` `||` `,` | `A::operator@(B)`       | operator@(A,B)      |
    | `a@b`       | `=` `+=` `-=` `*=` `/=` `%=` `^=` `&=` `|=` `<<=` `>>=` `[]`                        | `A::operator@(B)`       |                     |
    | `a(b,c...)` | `()`                                                                                | `A::operator()(B,C...)` |                     |
    | `a->b`      | `->`                                                                                | `A::operator->()`       |                     |
    | `(TYPE) a`  | `TYPE`                                                                              | `A::operator TYPE()`    |                     |
