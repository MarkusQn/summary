# Virtual member function
- A function must be defined `virtual` such that its behaviour can be modified in a subclass.

Example:

- assume that the base class and derived class have both a public or protected method with same signaure
- the fiollowing table shows with method is called

    | type pointer | type object | non virtual       | virtual           |
    | ------------ | ----------- | ----------------- | ----------------- |
    | Base*        | Base        | method of Base    | method of Base    |
    | Base*        | Derived     | method of Base    | method of Derived |
    | Derived*     | Derived     | method of Derived | method of Derived |

- A class that declares or inherits a virtual function is called a *polymorphic class*.

## Calling function of base class
- Within a subclass a function of the base class can be called by `base_class::function_name`
