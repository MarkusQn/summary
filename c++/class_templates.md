# Class templates
[c++ reference](https://en.cppreference.com/w/cpp/language/class_template)

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

## member templates
- template member function, possible within:
    - an ordinary (unparameterized) class
    - a class template
- restriction: not allowed to be virtual

### type inference
- member templates can be used for type inference.
- Example:
```C++
template <typename T1, typename T2>
struct pair {
  T1 first;  T2 second;
  ...
  template <typename U1, typename U2>
  pair(const pair<U1, U2> &p) : first(p.first), second(p.second) {}
};
```

- `U1`, `U2` must be convertible to `T1`, `T2` respective
- This constructor allows
```C++
city_to_state_map->insert(std::make_pair(city, state));
```

- instead of
```C++
city_to_state_map->insert(std::pair<char*, char*>(city, state));
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
