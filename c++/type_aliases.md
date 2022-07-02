# Type aliases

- Syntax:
```C++
typedef existing_type new_type_name ;
```
or
```C++
using new_type_name = existing_type ;
```
- `existing_type` is any type, either fundamental or compound
- A type alias is a different name by which a type can be identified. It does not create a new type, only an addirional name for the same.
- `typedef` and `using` are semantically equivalent, except `typedef` has certain limitations in the realm of templates
- Examples:
```C++
typedef unsigned int WORD;
typedef char * pChar;
typedef char field [50];

using WORD = unsigned int;
using pChar = char *;
using field = char [50]; 
```
