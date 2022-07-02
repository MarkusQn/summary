#C++ Precedence of operators
[c++ reference](https://en.cppreference.com/w/cpp/language/operator_precedence)


| Level  | Precedence group             | Operator                                                | Description                                       | LeftAssociativity | Right Associativity
| ------ | ---------------------------- | ------------------------------------------------------- | ------------------------------------------------- | ----------------- | -------------------
| 1      | Scope                        | `::`{: .diff_to_java }                                  | scope qualifier                                   | X                 |
| 2      | Postfix (unary)              | `++` `--`                                               | postfix increment / decrement                     | X                 |
|        |                              | `()`                                                    | functional forms                                  | X                 |
|        |                              | `[]`                                                    | subscript                                         | X                 |
|        |                              | `.` `->`{: .diff_to_java }                              | member access                                     | X                 |
| 3      | Prefix (unary)               | `++` `--`                                               | prefix increment / decrement                      |                   | X
|        |                              | `~` `!`                                                 | bitwise NOT / logical NOT                         |                   | X
|        |                              | `+` `-`                                                 | unary prefix                                      |                   | X
|        |                              | `&`{: .diff_to_java } `*`{: .diff_to_java }             | reference / dereference, see [pointer](pointer.md)          |                   | X
|        |                              | `new`[^1] `delete`{: .diff_to_java }                    | allocation / deallocation, see [dynamic memory](dynamic_memory.md) |                   | X
|        |                              | `sizeof`{: .diff_to_java }                              | [sizeof operator](sizeof_operator.md)                               |                   | X
|        |                              | `(type)`[^1]                                            | C-style type-casting                              |                   | X
| 4      | Pointer-to-member            | `.*`{: .diff_to_java } `->*`{: .diff_to_java }          | access pointer                                    | X                 |
| 5      | Arithmetic: scaling          | `*` `/` `%`                                             | multiply, divide, modulo                          | X                 |
| 6      | Arithmetic: addition         | `+` `-`                                                 | addition, subtraction                             | X                 |
| 7      | Bitwise shift                | `<<` `>>` [^2]                                          | shift left, shift right                           | X                 |
| 8      | Relational                   | `<` `>` `<=` `>=` [^3]                                  | comparison operators                              | X                 |
| 9      | Equality                     | `==` `!=`                                               | equality / inequality                             | X                 |
| 10     | And                          | `&`                                                     | bitwise AND                                       | X                 |
| 11     | Exclusive or                 | `^`                                                     | bitwise XOR                                       | X                 |
| 12     | Inclusive or                 | `|`                                                     | bitwise OR                                        | X                 |
| 13     | Conjunction                  | `&&`                                                    | logical AND                                       | X                 |
| 14     | Disjunction                  | `||`                                                    | logical OR                                        | X                 |
| 15     | Assignment-level expressions | `=` `*=` `/=` `%=` `+=` `-=` `>>=` `<<=` `&=` `^=` `|=` | assignment / compound assignment                  |                   | X
|        |                              | `?:`[^4]                                                | conditional operator                              |                   | X
| 16     | Sequencing                   | `,`{: .diff_to_java }                                   | [comma operator](comma_operator.md)                                | X                 |

[^1]: In Java `new` and `(type)` are in a own group just after the Prefix (3) group.
[^2]: In addition Java also has `>>>`
[^3]: In addition Java also has `instanceof`
[^4]: In Java `?:` is in a own group, just before the assignment