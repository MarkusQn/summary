# Inheritance

Syntax:

- after the class name add `:` followed by a comma-separated list of `base-specifiers`.
- `base-specifiers`: `access-specifier(optional) virtual-specifier(optional) base_class`
- `access- specifier`
    - is one of `public`, `protected`, `private`
    - defaults to `public`
    - limits the accessability of the inherited members
- `virtual`defines in the case of multiple inheritance with multiple path that variables exists only once

Example:
```C++
class Base {
  private:
    int val;
  public:
    void set (int a) { val=a; cout << "set a=" << a << '\n'; }
 };

class DerivedA: public Base {
 };

class DerivedB: private Base {
};
  
int main () {
  DerivedA a;
  DerivedB b;
  a.set (4);
//b.set (4);       // error: ‘Base’ is not an accessible base of ‘DerivedB’

//Base* base = &b; //  error: ‘Base’ is an inaccessible base of ‘DerivedB’
//base->set(9);
  return 0;
}
```

- By default a constructors of a derived class calls the default constructor of its base classes
- Calling a different constructor of a base class by using the following syntax (same as for initialize member variables):

```C++
derived_constructor_name (parameters) : base_constructor_name (parameters) {...}
```

Example:
```C++
class A {
  private:
    int valA;
  public:
    A(int a) : valA{a} { cout << "valA=" << valA << '\n'; }
 };

class B: public A {
  private:
    int valB;
  public:
    B(int a, int b) : A{a}, valB{b} {cout << "valB=" << valB << '\n';}
};

int main () {
  B b {2,3};
  return 0;
}
```

## Pointers to base class
- A **pointer** to a derived class is type-compatible with a pointer to its base class.

