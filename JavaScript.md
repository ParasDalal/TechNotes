- Variables declared within function as  "var" has function scope (even if they are declared in a block within function). If the variable is in the block of code, it gets "hoisted" as declared variable in the start of the function.
- If a variable is used without using "var" to declare it in the function, it turns into global scope variable
- Variable created with "let" has block scope - not available outside of the block in which it is declared.
- If an object is defined as "const", it's properties are not constant, and you cannot change the original value assigned to that variable, but you can change the properties of the object.
- 