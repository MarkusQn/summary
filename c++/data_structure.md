# Data structures

- Syntax:
```C++
struct type_name {
  member_type1 member_name1;
  member_type2 member_name2;
  member_type3 member_name3;
..
} object_names;
```
- `type_name` the name for the structure type
- `object_names` a set of valid identifiers for variables of that struct
- either `type_name` or `object_names` can be left away
- Struct can be nested (contain other struct)

## member of object operator `.`
- A member can be accessed by dot `.`, example: `apple.weight`

## arrow operator (->)
- If we have a pointer to a struct, the member can be accessed with the arrow operator (->)
- `pmovie->title` is equivalent to `(*pmovie).title`