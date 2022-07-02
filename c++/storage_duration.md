# Storage duration

- **automatic** storage duration
    - allocated at the beginning of the enclosing code block and deallocated at the end.
    - Stored on the *stack*
    - local objects have this storage duration, except those declared `static`, `extern` or `thread_local`.

- **dynamic** storage duration
    - allocated and deallocated upon request by using [[dynamic memory]] allocation functions
    - Stored on the *heap*
    - Stack allocation is simpler - and much faster! - than heap allocation. 
    - @Google: normally don't call `new` or `delete` directly. Use `std::make_unique` and `std::unique_ptr`, see [[smart pointer]]

- **static** storage duration
    - allocated when the program begins and deallocated when the program ends.
    - objects declared at namespace scope (including global namespace) have this storage duration, plus those declared with `static` or `extern`.
    - variables have static storage duration if not marked as `thread_local` and:
        - declared at namespace [[scope]] (including global namespace)
        - `static` data member of a class
        - `static` variable defined in a function
    - @Google: discourages the use of global mutable state, better use `constexpr`
    - Variables with built-in or struct/class types *without* constructors (or with constexpr constructors) initialized with compile-time constants are initialized before any code runs.
    - Variables with (non-trivial, non-constexpr) constructors
        - are said to be dynamically initialized because code needs to run in order to set their initial state. This initialization code is run top-down within a file
        - Destructors for these variables are also executed in an undefined order

- **thread** storage duration
    - allocated when the thread begins and deallocated when the thread ends.
    - Each thread has its own instance of the object.
    - Only objects declared `thread_local` have this storage duration.
        - declared at namespace scope
        - static class members
        - inside functions
    - `thread_local` variables are subject to the same initialization-order issues as static variables (and more besides)