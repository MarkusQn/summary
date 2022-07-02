# Namespaces

- Groups named entities that otherwise would have *global [scope](scope.md)* into narrower scopes, giving them *namespace scope*

## Definition
- Syntax
```C++
namespace identifier
{
  named_entities
}
```
- identifier is any valid identifier
- `named_entities` is the set of [variable](variable.md)s, types and [function](function.md)s
- Multiple above definition blocks can exist for the same namespace, even across different translation units (i.e., across different files of source code).

## Accessing entities
- The entities of an namespace can be accessed
    - from within their namespace: normally, with `EntityIdentifier`
    - from outside the namespace: with qualified access in the form `NamespaceIdentifier::EntityIdentifier`
- The keyword `using` introduces into the *global [scope](scope.md)* (defined outside of blocks) or into the current *block [scope](scope.md)*: 
    - a single named entity wirh `using NamespaceIdentifier::EntityIdentifier;`
    - all named entities of an namespace with `using namespace NamespaceIdentifier;`
- Multiple `using` possible

## Namespace aliasing
- Existing namespaces can be aliased with `namespace new_name = current_name;`

## The std namespace
- All entities (variables, types, constants, and functions) of the standard C++ library are declared within the `std` namespace.