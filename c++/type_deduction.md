## Type deduction

## auto
- The compiler figure out the type of a variable by the initializer.
```c++
int foo = 0;
auto bar = foo;  // the same as: int bar = foo;
```

- Can be used to remove redundancies when constructing objects.
```c++
// without auto
diagnostics::ErrorStatus* status = new diagnostics::ErrorStatus("xyz");
// with auto
auto* status = new diagnostics::ErrorStatus("xyz");
```

- Can be used for simplifying the element type of an iteration.
```c++
// widthout auto
for (const std::pair<const std::string, double>& entry : dictionary) {
  printf("%f\n", entry.second);
}

// with auto
for (const auto& entry : my_map) {
  printf("%f\n", entry.second);
}
```

- auto is a type specifier (like `int` or `float`) and can be combined with `const`, `*`, `&`

| Declaration                        | Meaning
| ---------------------------------- | ---------
| `auto x = f();`                    | Mutable variable, initialized by copying. mutable even if `f()`'s return value is `const`
| `const auto x = y;`                | Immutable variable, initialized by copying
| `const auto& x = v[i];`            | Avoids copying
| `auto& x = *iter;`                 | Avoids copying, lets you modify the referenced object
| `const auto* p = new MyClass;`     | Disallow mutation of pointed-to object
| `const auto* const p = new MyCls;` | Disallow mutation of pointed-to object, disallow changing the variable itself


## decltype
- Variables without initializer can also make use of type deduction with the decltype specifier.
```c++
int foo = 0;
decltype(foo) bar;  // the same as: int bar; 
```