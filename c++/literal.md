# Literals

- express particular values within the source code

## Integer literals
[c++ reference](https://en.cppreference.com/w/cpp/language/integer_literal)

- Data Type:
    - Default: `int` or <span class="diff_to_java">next higher in which the value can fit</span>
    - <span class="diff_to_java">Suffix `u` or `U`: `unsigned`</span>
    - Suffix `l` or `L` : `long` or <span class="diff_to_java">next higher in which the value can fit</span>
    - <span class="diff_to_java">Suffix `ll` or `LL`: `long long`</span>
    - Note: `u`/`U` can be combind with `l`/`L`/`ll`/``LL``
- Syntax:
    - Default: **decimal-literal** (base 10)
    - Prefix `0`: **octal-literal** (base 8)
    - Prefix `0x` or `0X`: **hex-literal** (base 16), hex digits (a..f) may be lower- or upper-case.
    - Prefix `0b` or `0B`: **binary-literal** (base 2), since C++14
- <span class="diff_to_java">Optional single quotes (') may be inserted between the digits as a separator.</p>

## Floating literals
[c++ reference](https://en.cppreference.com/w/cpp/language/floating_literal)

- Data Type:
    - Default: `double`
    - Suffix `f` or `F`: `float`
    - <span class="diff_to_java">Suffix `l` or `L`: `long double`</span>
- Syntax
    - Contains either or both of
        - decimal-exponent `e` or `E` Example: `1e1'`
        - decimal separator `.` Example: `3.14`, `1.`
    - <span class="diff_to_java">Prefix `0x` or `0X`: **hex-literal** (C++17)</span>
        - must contain `p` or `P` as an hex-exponent (instead of `e` or `E`)

## Boolean literals
[c++ reference](https://en.cppreference.com/w/cpp/language/bool_literal)

- Data Type: `bool`
- Syntax: value `true` or `false`

## Character literal
[c++ reference](https://en.cppreference.com/w/cpp/language/character_literal)

- Enclosed in single quotes (')
- Data Type:
    - Default `char`
    - <span class="diff_to_java">Prefix `u8`: UTF-8 character literal `char` (before C++20) `char8_t` (C++20), e.g. `u8'a'` (C++17)</span>
    - <span class="diff_to_java">Prefix `u`: `char16_t`, e.g. `u'a'` (C++11)</span>
    - <span class="diff_to_java">Prefix `U`: `char32_t`, e.g. `U'a'` (C++11)</span>
    - <span class="diff_to_java">Prefix `L`: `wchar_t`, e.g. `L'a'`</span>
- Syntax
    - Normal character
    - Escape Code according to table below

Escape code	| Description
------------|------------
\n          | newline
\r          | carriage return
\t          | tab
\v          | <span class="diff_to_java">vertical tab</span>
\b          | backspace
\f          | form feed (page feed)
\a          | <span class="diff_to_java">alert (beep)</span>
\'          | single quote (')
\"          | double quote (")
\?          | <span class="diff_to_java">question mark (?)</span>
\\          | backslash (\)
\nnn        | <span class="diff_to_java">octal value nnn</span>
\xnn        | <span class="diff_to_java">hexadecimal value nn</span>
\unnnn      | unicode value nnnn
\Unnnnnnnn  | <span class="diff_to_java">unicode value nnnnnnnn</span>

## String literal
[c++ reference](https://en.cppreference.com/w/cpp/language/string_literal)

- Enclosed in  double quotes (")
- Data Type:
    - Default `const char[N]`
    - <span class="diff_to_java">Prefix `u8`: UTF-8 string literal `const char[N]` (before C++20)  `const char8_t{N]` (C++20) , e.g. `u8'a'` (C++17)</span>
    - <span class="diff_to_java">Prefix `u`: `const char16_t[N]`, e.g. `u'a'` (C++11)</span>
    - <span class="diff_to_java">Prefix `U`: `const char32_t[N]`, e.g. `U'a'` (C++11)</span>
    - <span class="diff_to_java">Prefix `L`: `const wchar_t[N]`, e.g. `L'a'`</span>
- Syntax
    - Normal characters
    - Escape Code according to table above
- Multiple consecutive String literals seperated by whitespace (including tabs, newlines) are concateneded with a blank in between e.g. `"one" "two"` same as `"one two"` 
- Are null terminated char arrays, of type `const char`

## nullptr
[c++ reference](https://en.cppreference.com/w/cpp/language/nullptr)

- Syntax: value `nullptr`
