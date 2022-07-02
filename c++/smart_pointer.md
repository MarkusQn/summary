# Smart pointers
- automatic memory management, release resources if the smart pointers get out of scope.

## unique_ptr
- Only one reference to target
- The referenced object gets deleted when ptr out of scope
- Cannot be copied
- created either
    - calling constructor and wrapping it
    - calling `std::make_unique<*type*>(*parameter-list*);
- Can be dereferenced like normal pointers
- no overhead in space and time compared to raw pointers
- can also be used for arrays `std::unique_ptr<T[]>`

Example:
```c++
#include <iostream>
#include <memory>
#include <string>

class Entity {
  std::string n;
public:
  Entity(std::string name) {
    n = name;
    std::cout << "created " << n << std::endl;
  }
  ~Entity() {
    std::cout << "deleted " << n << std::endl;
  }
};

int main() {

  {
    // call constructor and wrap it
    std::unique_ptr<Entity> sm_ptr(new Entity("one"));
    // call make_shared
    std::unique_ptr<Entity> sm_ptr2 = std::make_unique<Entity>("two");
  }
  std::cout << "end" << std::endl;
}
```

## shared_ptr
- Can be copied such that multiple shared pointers to the referenced object exist
- Uses internal reference counter, when counter gets to 0, the referenced object is deleted
- reference counter is kept in control block
- Created either
    - calling constructor and wrapping it
    - calling `std::make_shared<*type*>(*parameter-list*);
- Can be dereferenced like normal pointers

Example:

```c++
#include <iostream>
#include <memory>
#include <string>

class Entity {
  std::string n;
public:
  Entity(std::string name) {
    n = name;
    std::cout << "created " << n << std::endl;
  }
  ~Entity() {
    std::cout << "deleted " << n << std::endl;
  }
};

int main() {

  {
    std::shared_ptr<Entity> sm_ptr1;
    {
      // call constructor and wrap it
      std::shared_ptr<Entity> sm_ptr(new Entity("one"));
      // call make_shared
      std::shared_ptr<Entity> sm_ptr2 = std::make_shared<Entity>("two");
      sm_ptr1 = sm_ptr2;
    }
    std::cout << "end inner" << std::endl;
  }
  std::cout << "end outer" << std::endl;
}
```

output:
```
created one
created two
deleted one
end inner
deleted two
end outer
```

## weak_ptr
- a non-owning ("weak") reference to an object that is managed by `std::shared_ptr`
- dosn't increase reference count
- must be converted to `std::shared_ptr` to access the referenced object.