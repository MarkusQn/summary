# Const member functions
- When an object (variable, parameter) of a class is qualified as a `const`:
```C++
const MyClass myobject;
```
- access to members restricted as follows
    - data member
        - restricted to read-only (from outside the class), also to member of members (and so on)
    - member functions:
        - only callable if declared as const member
        - done by adding `const` keyword following the function prototype, example `int get() const {return x;}`
        - Note: `const` before the return type, qualifies the type returned as const
        - const Member functions cannot
            - modify non-static data members nor 
            - call other non-const member functions 
        - const members shall not modify the state of an object.
        - Member functions can be overloaded on their constness: i.e., a class can have two member functions with identical signatures except that one is const and the other is not
- const classes often used as parameter to function `void print (const MyClass& arg) {...}`

Example of const
```C++
class A {
  public:
    int x;
    A(int val) : x(val) {}
    int get() const {return x;}
    void set(int v) { x = v;}
};

int main() {
  A a(10);
  a.x = 20;
  cout << a.x << '\n';
  a.set(30);
  cout << a.get() << '\n';

  const A ac(10);
//ac.x = 20;                 // not valid: x cannot be modified
  cout << ac.x << '\n';      // ok: x can be read
//ac.set(30);                // not valid: set() is not const
  cout << ac.get() << '\n';  // ok: data member get() is const
  return 0;
}
```
