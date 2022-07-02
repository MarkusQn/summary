# Container
- a collection of objects of some object type T
- all containers are [[class templates]] that are parameterized at least by the type of the values that they will store
- two broad classes of containers
    - sequence-based
        - most important:
            - `std::vector`: similar to C arrays, but dynamically-resizable
            - `std::list` / `std::forward_list`: a linked list of values
            - `std::deque`: similar to vector, but constant time insert/removal on both side + provides element pointer stability after insert/removal at the ends
        - less important:
            - `absl::InlinedVector`: similar to vector, but can maintain a small number of elements without allocation. 
            - `absl::Span`:  non-owning view onto a contiguous collection of data
    - associative
        - hash based
            - most important:
                - `absl::flat_hash_map`: unordered collection that maps key -> value
                - `absl::flat_hash_set`: unordered collection of unique values
            - less important:
                - `absl::node_hash_map`: uses separate allocations for the key and value, thus providing pointer stability
                - `absl::node_hash_set`: uses separate allocations for the entries, thus providing pointer stability
                - `std::unordered_map`: similar to `absl::flat_hash_map`, provided by the standard but significantly less performant.
                - `std::unordered_set`: similar to `absl::flat_hash_set`, provided by the standard but significantly less performant.
        - ordered
            - most important:
                - `absl::btree_map`: ordered  collection that maps key -> value
                - `absl::btree_set`: ordered collection of unique values
            - less important:
                - `std::map`: similar to `absl::btree_map`, provided by the standard but significantly less performant.
                - `std::set`: similar to `absl::btree_set`, provided by the standard but significantly less performant.

## Iterating Over Containers
- prefered way: range based for loop
```C++
for (double w : weights) {
   sum += w;
}
```

- some container support index based access
```C++
for (int i = 0; i < weights.size(); ++i) {
   sum += weights[i];
}
```

- iterators are a generalization of a pointer
    - there are `iterator` and `const_iterator`
    - `begin()` returns iterator to first element in container.
    - `end()` returns iterator pointing just **past** last element in container
    - example loop:
```C++
for (std::vector<double>::const_iterator it = weights.begin(); it != weights.end(); ++it) {
  sum += *it;
}
```

## Mutating Containers
- for a data structure to be thread safe, it needs to satisfy at least one of the three "IIS" conditions:
    - be **I**mmutable (i.e., read-only)
    - be **I**solated in that all accesses/mutations are limited to a single thread
    - use proper **S**ynchronization primitives to guarantee mutual exclusion
- Important member functions:
    - `push_back`: Add an element to the end
    - `pop_back`: Remove an element from the end
    - `push_front`: Insert an element at the beginning
    - `pop_front`: Remove an element from the beginning
    - `insert`: Insert element(s) at an arbitrary location
    - `erase`: Erase element(s)
    - `clear`: Empties the container
- non-member functions defined in the standard header `<algorithm>`
    - `copy`
    - `fill`
    - `generate`
    - `swap`
    - `transform`
    - `replace` {, `_if`, `_copy`, `_copy_if`}
    - `remove` {, `_if`, `_copy`, `_copy_if`}
    - `reverse`
    - `rotate`
    - `random_shuffle`
    - `sort`
- changing the container has an impact on existing iterators that point at elements in the container
    - Example: erasing an element in an associative container invalidates all iterators that point to **that** element.