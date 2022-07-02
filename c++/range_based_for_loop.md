# Range-based for loops
- allows to iterate through the elements of a collection
- Syntax
```C++
for (<variable declaration> : <collection>)
  <loop body>
```
- Range-based for works with any of the usual collection types, including STL containers.
- Example that also avoids making copies by using `const` reference
```C++
std::map<std::string, int> numbers = {{"zero", 0}, {"one", 1}, {"two", 2}};
for (const auto& p : numbers) {
  LOG(INFO) << p.first << ": " << p.second;
}
```

- Range loop requires either
    - an expression of array type or
    - an expression of a class type C that has `begin()` and `end()` method, the corresponding code for a range-based for loop is:
```C++
for (auto iter = <collection>.begin(), last = <collection>.end();
     iter != last;
     ++iter) {
  <variable declaration> = *iter;
  <loop body>
}
```