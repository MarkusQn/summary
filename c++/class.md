# Classes

see also: [[operator overloading]], [[special member functions]], [[inheritance]], [[virtual member function]], [[abstract_class]], [[const member functions]]

## Definition

- classes defined either with keyword `class`, `struct` or `union`
```C++
class class_name {
  access_specifier_1:
    member1;
  access_specifier_2:
    member2;
  ...
} object_names;
```
- object_names optional
- members are data or function declarations
- a function can be specified in the class definition:
    - full function definition including body 
    - only prototype, the full function including body outside defined, with prefix `class_name::`
    - the only difference: the full function will be considered an `inline` member function
- access_specifier:
    - `private`: accessible from within same class and from their "friends".
    - `protected` : accessible from within same class, from their "friends" and subclasses.
    - `public`: accessible from anywhere where the object is visible.
    - when `class` default `private`
    - when  `struct` / `union` default  `public`
- Friends
    - friend function: add signature of function in class with keyword `friend`
    - friend class: add class name in class with keyword `friend`
    - a friends definition is for one direction
    - friends relationships are not transitive (friend of a friend is not a friend)
    - a subclass of a friend has no access
Example:
```C++
class Rectangle {
    friend Rectangle duplicate (const Rectangle&);
    ...
};

Rectangle duplicate (const Rectangle& param)
{
    ...
}

class Square {
  friend class Rectangle;
  ...
};
```

## (forward) Declaration
- Declares that a class exists
- used when two class definitions need reference each other
- Syntax keyword `class class_name;`

## Member access
- outside the class
    - members are accessed with the dot `object_name.member_name` like in [[data structure]]
- from a member function
    - `member_name`
    - `this->member_name`

Example:
```C++
#include <iostream>
using namespace std;

class Rectangle {
    int width, height;
  public:
    void set_values (int,int);
    int area() {return width*height;}
};

void Rectangle::set_values (int x, int y) {
  width = x;
  height = y;
}

int main () {
  Rectangle rect;
  rect.set_values (3,4);
  cout << "area: " << rect.area();
  return 0;
}
```

## Constructors
- Constructor function declared like regular member function, but with a name that matches the class_name and without return type
- Constructor can also be overloaded
- Calling  Constructor
    - Constructors cannot be called like normal function, only executed once, when a new object of that class is created.
    - 3 forms to call an constructor:

        | Name                              | Syntax                                                                  | Example                                            |
        | --------------------------------- | ----------------------------------------------------------------------- | -------------------------------------------------- |
        | *functional form*                 | `class_name object_name (value1, value2, ... );`                        | `Rectangle rect (3,4);`                            |
        | *variable initialization syntax*  | `class_name object_name = initialization_value;` (only if single param) | `Circle bar = 20.0;`                               |
        | *uniform initialization*          | `class_name object_name { value1, value2, ... };` (optional with `=`)   | `Circle bar {30.0};`<br> `Circle bar = {40.0};`    |

## Member initialization in constructors
- members can be initialized before executing the body by inserting before the constructor's body, a colon (:) and a list of initializations for class members.
- *functional form* or *uniform initialization*
```C++
Rectangle::Rectangle (int x, int y) { width=x; height=y; }

// can be written as 
Rectangle::Rectangle (int x, int y) : width(x), height(y) { }

// or also as
Rectangle::Rectangle (int x, int y) : width(x) { height=y; }
```
- for members of fundemental types
    - it does not make a difference, because they are not initialized by default
- for member objects (of type class)
    - if they are not initialized after the colon, they are default-constructed
    - if no default constructor: members must be initialized in the member initialization list

## Pointers to classes
- Objects can also be pointed to by pointers
- Example `Rectangle * prect;`
- Same as with [[data structure]], members can than be accessed using the arrow operator (->) `foo->area();`
Example:
```C++
  Rectangle obj (3, 4);
  Rectangle * foo, * bar, * baz;
  foo = &obj;
  bar = new Rectangle (5, 6);
  baz = new Rectangle[2] { {2,5}, {3,6} };
  delete bar;
```

## keyword this
- keyword this represents a **pointer** to the object whose member function is being executed.
- Example:
```C++
CVector& CVector::operator= (const CVector& param)
{
  x=param.x;
  y=param.y;
  return *this;
}
```

## Static members
- A class can contain static members, either data (aka "class variable") or functions.
- They are marked with `static`
- static members can be referred to as a member of any object of that class or even directly by the class name
```C++
cout << a.n;
cout << Dummy::n;
```
- static variable
    - cannot be initialized directly in the class, but need to be initialized somewhere outside it.
```C++
class Dummy {
  public:
    static int n;
    Dummy () { n++; };
};

int Dummy::n=0;
```
- static functions
    - cannot access non-static members of the class (neither member variables nor member functions)
    - cannot use the keyword `this`

