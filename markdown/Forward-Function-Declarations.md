Next: [Static Functions](Static-Functions.md), Previous: [Function
Parameter Variables](Function-Parameter-Variables.md), Up: [Function
Definitions](Function-Definitions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 22.1.2 Forward Function Declarations 


The order of the function definitions in the source code makes no
difference, except that each function needs to be defined or declared
before code uses it.

The definition of a function also declares its name for the rest of the
containing scope. But what if you want to call the function before its
definition? To permit that, write a compatible declaration of the same
function, before the first call. A declaration that prefigures a
subsequent definition in this way is called a *forward declaration*. The
function declaration can be at top level or within a block, and it
applies until the end of the containing scope.

See [Function Declarations](Function-Declarations.md), for more
information about these declarations.
