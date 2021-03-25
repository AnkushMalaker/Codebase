## Scope of variable

This is tricky to get a hold of at the beginning easy to get a hang of once you start using it. The best way to do it is to practice with some sample programs and implementing simple loops or functions. Reading the (documentation)[https://docs.julialang.org/en/v1/manual/variables-and-scoping/] for this is **absolutely** essential.  

The below info is directly from there:  
### Scope constructs:  

|                                  Construct |   Scope type |  Allowed within |
|-------------------------------------------:|-------------:|----------------:|
|                         module, baremodule |       global |          global |
|                                     struct | local (soft) |          global |
|                            for, while, try | local (soft) | global or local |
|                                      macro | local (hard) |          global |
| let, functions, comprehensions, generators | local (hard) | global or local |


>When x = \<value> occurs in a local scope, Julia applies the following rules to decide what the expression means based on where the assignment expression occurs and what x already refers to at that location:
>
>1. Existing local: If x is already a local variable, then the existing local x is assigned;
>2. Hard scope: If x is not already a local variable and assignment occurs inside of any hard scope construct (i.e. within a let block, function or macro body, comprehension, or generator), a new local named x is created in the scope of the assignment;
>3. Soft scope: If x is not already a local variable and all of the scope constructs containing the assignment are soft scopes (loops, try/catch blocks, or struct blocks), the behavior depends on whether the global variable x is defined:
>if global x is undefined, a new local named x is created in the scope of the assignment;
>if global x is defined, the assignment is considered ambiguous:
>in non-interactive contexts (files, eval), an ambiguity warning is printed and a new local is created;
>in interactive contexts (REPL, notebooks), the global variable x is assigned.
>
>You may note that in non-interactive contexts the hard and soft scope behaviors are identical except that a warning is printed when an implicitly local variable (i.e. not declared with local x) shadows a global. In interactive contexts, the rules follow a more complex heuristic for the sake of convenience. This is covered in depth in examples that follow.


