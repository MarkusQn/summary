# Fundamental data types
[c++ reference](https://en.cppreference.com/w/cpp/language/types)

## Character types

Type names 	  | Notes on size / precision
--------------|-------------------------------------------
`char`        | Exactly one byte in size. At least 8 bits.
`char16_t`    | Not smaller than `char`. At least 16 bits.
`char32_t`    | Not smaller than `char16_t`. At least 32 bits.
`wchar_t`     | Can represent the largest supported character set.

## Integer types

Signed type names              | Unsigned type names          | Notes on size / precision
-------------------------------|------------------------------|-----------------------------------------
`signed char`                  | `unsigned char`              | Same size as char. At least 8 bits.
*`signed`*` short `*`int`*     | `unsigned short `*`int`*     | Not smaller than `char`. At least 16 bits.
*`signed`*` int`               | `unsigned `*`int`*           | Not smaller than `short`. At least 16 bits.
*`signed`*` long `*`int`*      | `unsigned long `*`int`*      | Not smaller than `int`. At least 32 bits.
*`signed`*` long long `*`int`* | `unsigned long long `*`int`* | Not smaller than `long`. At least 64 bits.

*`kursiv`* is optional, can be omitted

## Floating-point types

Type names    | Notes on size / precision
--------------|------------------------------
`float`       | 
`double`      | Precision not less than `float`
`long double` | Precision not less than `double`

## Boolean type

Type names    | Notes on size / precision
--------------|------------------------------
`bool`        |

## Void type

Identifies the lack of type

Type names    | Notes on size / precision
--------------|------------------------------
`void`        | no storage

## Null pointer

A special type of pointer

Type names          | Notes on size / precision
--------------------|------------------------------
`decltype(nullptr)` |

## Sizes / fixed sizes

 * The `numeric_limits` classes (in header `<limits>`) return properties of fundamental types
 * The header `<cstdint>` defines  types of specific sizes (e.g. `uint32_t`)