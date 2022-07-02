# Reference

- A reference is like a const pointer that’s automatically dereferenced (has a * in front of it) each time it’s used.
- Reference is never NULL
- Cannot be reassigned to point to something different
- A reference is a lvalue.

- *lvalue reference*
    - reference to an lvalue (see [[value category]])
    - Declaration: `int& lref = a;`
    - Use:
        - alias to an existing object
        - to implement pass-by-reference semantics

- *rvalue reference*
    - reference to an rvalue (see [[value category]])
    - Declaration: `int&& rref = 20;`
    - extend the lifespan of the temporary object to which they are assigned
    - Non-const rvalue references allow you to modify the rvalue.
    - Use:
        - with the move constructor and move assignment.

- Note:
    - lvalue references can be assigned with the rvalues but 
    - rvalue references cannot be assigned to the lvalue. 