# Copy assignment
[c++ reference](https://en.cppreference.com/w/cpp/language/copy_assignment)

- An overload of `operator=` which takes a value or reference of the class itself as single parameter.
- The return value is generally a reference to `*this`, although this is not required

Example:
```C++
Example5& operator= (const Example5& x) {
  *ptr = x.content();
  return *this;
}
```

- Implicitly defined, if a class has no custom copy nor move assignments (nor move constructor) defined.
- Implicit definition performs a shallow copy 
- called on assignment

```C++
MyClass foo;             // default constructor called
MyClass bar (foo);       // copy constructor called
MyClass baz = foo;       // copy constructor called
foo = bar;               // copy assignment called
```
