http://eel.is/c++draft/dcl.init#21

Destroying a reference ends the lifetime of the reference. Destroying a variable destroys the entity to which it refers; if no such entity exists, the behavior is undefined.

http://eel.is/c++draft/basic.life#2

The lifetime of a reference ends when it is destroyed.

http://eel.is/c++draft/stmt.jump#2

On exit from scope, variables with automatic storage duration declared inside that scope through which control has passed are destroyed in the reverse order of their declaration. Transfer out of a loop, out of a block, or back past an initialized variable with automatic storage duration involves the destruction of variables with automatic storage duration that are in scope at the point transferred from but not at the point transferred to.
