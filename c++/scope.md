# Scope

- Named entities (e.g. [variable](variable.md)s, [function](function.md)s, and compound types) need to be declared before being used
- An entity declared outside any block has *global scope*
    - meaning that its name is valid anywhere in the code
- An entity declared directly within a [namespace](namespace.md) block has *namespace scope*
- An entity declared within a block `{ }` has *block scope*
    - only visible until the end of the block, including inner blocks
    - [variable](variable.md)s with block scope are known as *local variables*
    - [variable](variable.md)s declared in declarations that introduce a block, are local to that block, this includes:
         - [function](function.md) parameters
         - variables declared in loops and conditions (such as those declared on a for or an if) 
- Multiple Occurence
    - In each scope, a name can only represent one entity
    - An inner block can define a new entity with a name existing in an outer scope, *hiding* the entity outside.
