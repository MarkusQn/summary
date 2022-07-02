# Lambda
- Syntax
```C++
[ captures ] ( params ) specs { body }
```
- a lambda is an unnamed [[function object]] capable of capturing variables in scope.
    - `captures` corresponds to member variables of [[function object]]
    - `params` corresponds to parameter of `operator()`
    -  return type corresponds to return type of `operator()`
    - `body` corresponds to body of `operator()`
- Example:
```C++
if (absl::c_any_of(candidates, [](int x) { return x == 2; })) {
  std::cout << "target found\n";
}
```

- **captures**
    - "capture" of local variables (or of this), either by value or by reference
    - Syntax:
        - `[]`: Nothing is captured
        - `[=]`: any local variable used is captured copy
        - `[&]`: any local variable used is captured reference
        - `[x]`: x is captured by value (i.e., a copy is made).
        - `[x, &y]`: x is captured by value, y is captured by reference.
        - `[=, &y]`: y is captured by reference, any other local variable used is captured by value.
        - `[&, x]`: x is captured by value, any other local variable used is captured by reference.
    - Capturing by reference does not affect its lifetime -> can create dangling references. Therfore a lambda returned from a (non-lambda) function should not capture by reference.
    - Variables captured by value are `const` by default, use `mutable` specifier to overwrite
    - `this` pointer of current object can be explicitly or implicitly captured
- **params**
    -  list of parameters, can be omitted (including its parentheses) if there are no parameters.
- **specs** consist of the following specifier in that order, each is optional
    - *specifiers*
        - `mutable`: allows body to modify the objects captured by copy, and to call their non-const member functions
        - `constexpr`: explicite define function as constexpr
    - *exception*: provides the noexcept specifier for operator()
    - *attr*: Specifies attributes
    - *trailing-return-type*
        - `-> <ret>`, where `<ret>` specifies the return type.
        -  If omitted: the compiler will deduce it as long as all of the lambda's return statements return the same type
- A lambda that captures nothing can be converted to a function pointer. Example:
```C++
int (*square)(int) = [](int x) { return x * x; };
```

- To pass a lambda as an parameter, `std::function` can be used:
```C++
template<class InputIterator>
int count_if (InputIterator first, InputIterator last, std::function<bool(int)> pred)
{
  int result = 0;
  while (first!=last) {
    if (pred(*first)) result++;
    ++first;
  }
  return result;
}

int main () {
  std::array<int,7> foo = {0,1,-1,3,-3,5,-5};

  int threshold = 1;
  std::cout << "Numbers smaller than " << threshold << ": "
        << count_if(foo.begin(), foo.end(), [threshold](int i)->bool{return i < threshold;})
        << std::endl;
}
```
