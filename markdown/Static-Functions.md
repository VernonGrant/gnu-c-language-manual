Next: [Arrays as Parameters](Arrays-as-Parameters.md), Previous:
[Forward Function Declarations](Forward-Function-Declarations.md), Up:
[Function Definitions](Function-Definitions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 22.1.3 Static Functions 


The keyword `static` in a function definition limits the visibility of
the name to the current compilation module. (That's the same thing
`static` does in variable declarations; see [File-Scope
Variables](File_002dScope-Variables.md).) For instance, if one
compilation module contains this code:

``` C
static int
foo (void)
{
  …
}
```

then the code of that compilation module can call `foo` anywhere after
the definition, but other compilation modules cannot refer to it at all.


To call `foo` before its definition, it needs a forward declaration,
which should use `static` since the function definition does. For this
function, it looks like this:

``` C
static int foo (void);
```

It is generally wise to use `static` on the definitions of functions
that won't be called from outside the same compilation module. This
makes sure that calls are not added in other modules. If programmers
decide to change the function's calling convention, or understand all
the consequences of its use, they will only have to check for calls in
the same compilation module.
