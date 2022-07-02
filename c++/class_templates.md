# Class templates
- class templates allow classes to have members that use template parameters as types.
- function definition (containing body) outside of the class definition must contain also the class template parameters.
- A template class can be used bz providing the template arguments in `< .. >`

```C++
template <class T> class MyPair {
    T a, b;
  public:
    MyPair (T first, T second) {a=first; b=second;}
    T getmax ();
};

template <class T> T MyPair<T>::getmax ()
{
  T retval;
  retval = a>b? a : b;
  return retval;
}

int main () {
  MyPair <int> myobject (100, 75);
  cout << myobject.getmax();
  return 0;
}
```

## Template specialization
- Define a different implementation for a template when a specific type is passed as template argument.
- precede the class name with `template<>`
- Add the specialization parameter after the class template name

```C++
template <class T> class mycontainer { ... }; // generic template
template <> class mycontainer <char> { ... }; // specialization.
```
- When declaring a specializations, all members must be provided (no inheritance of members from generic template to the specialization)
