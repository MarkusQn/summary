# Function templates
[c++ reference](https://en.cppreference.com/w/cpp/language/function_template)

## Define template function
- Syntax:
```C++
template < TemplateParameterList > FunctionDefinition
```
- `TemplateParameterList`
    - comma seperated list of template parameters
- template parameters can be types:
    - These parameters are generic template types `class` or `typename` followed by an identifier
    - `class` or `typename` are synonyms 
    - The generic type can be used in [function](function.md)s as
        - parameter type
        - return type
        - [variable](variable.md) declaration
    - Example:
```C++
template <class T>
T add (T a, T b)
{
  T result;
  result = a + b;
  return result;
}
```
- template parameters can also be values
    - Therefore the type is specified followed by the identifier
    - Example:
```C++
template <class T, int N>
T fixed_multiply (T val)
{
  return val * N;
}
```

## Call template function
- Syntax:
```C++
FunctionName < TemplateArguments > ( FunctionArguments )
```
- `TemplateArguments` used to instantiates a version of the function by the compiler
- `TemplateArguments` can be omited if the type can be unambiguous deduced
- If the template parameter is a value it must be
    - provided
    - possibe to be determined on compile-time
- Example:
```C++
k = add<int> (i,j);
h = add<double> (f,g);

int i = 1;
int j = 2;
int k;
k = add (i,j);    // template parameter deduced by the compiler

int l = fixed_multiply<int,2>(10);
```
