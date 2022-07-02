# Unions

- Syntax:
```C++
union type_name {
  member_type1 member_name1;
  member_type2 member_name2;
  member_type3 member_name3;
  .
  .
} object_names;
```
- Unions allow one portion of memory to be accessed as different data types.
- The size of this type is the one of the largest member element.

## Anonymous unions

- When unions are members of a class or structure, they can be declared with no name.
- The members are than directly accessible from objects by their member names.
- Example:
```C++
struct book2_t {
  char title[50];
  char author[50];
  union {
    float dollars;
    int yen;
  };
} book2;

// access the member
book2.dollars

// if the union would have been declared with a object_names `price`
book2.price.dollars
```
