# Function Object

- A function object, also known as a "functor", is an object that has an `operator()` defined, so that it can be called with function call syntax.
- Example:
```C++
class HasTargetValue {
public:
  explicit HasTargetValue(int target) : target(target) {}
  bool operator()(int candidate) const { return candidate == target; }
private:
  int target;
};

...
std::vector<int> candidates = {1, 2, 7};
if (absl::c_any_of(candidates, HasTargetValue(2))) {
  std::cout << "target found\n";
}
```