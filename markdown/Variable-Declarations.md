Next: [Initializers](Initializers.md), Up: [Variables](Variables.md)
 
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 20.1 Variable Declarations 


Here's what a variable declaration looks like:

``` C
keywords basetype decorated-variable [= init];
```

The `keywords` specify how to handle the scope of the
variable name and the allocation of its storage. Most declarations have
no keywords because the defaults are right for them.

C allows these keywords to come before or after `basetype`,
or even in the middle of it as in `unsigned static int`, but don't do
that---it would surprise other programmers. Always write the keywords
first.

The `basetype` can be any of the predefined types of C, or a
type keyword defined with `typedef`. It can also be `struct tag`,
`union tag`, or `enum tag`. In addition, it can include type qualifiers
such as `const` and `volatile` (see [Type
Qualifiers](Type-Qualifiers.md)).

In the simplest case, `decorated-variable` is just the
variable name. That declares the variable with the type specified by
`basetype`. For instance,

``` C
int foo;
```

uses `int` as the `basetype` and `foo` as the
`decorated-variable`. It declares `foo` with type `int`.

``` C
struct tree_node foo;
```

declares `foo` with type `struct tree_node`.

-   [Declaring Arrays and Pointers](Declaring-Arrays-and-Pointers.md)
-   [Combining Variable
    Declarations](Combining-Variable-Declarations.md)
