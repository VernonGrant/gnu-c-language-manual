Next: [Macro Pitfalls](Macro-Pitfalls.md), Previous: [Undefining and
Redefining Macros](Undefining-and-Redefining-Macros.md), Up:
[Macros](Macros.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.5.9 Directives Within Macro Arguments 


GNU C permits and handles preprocessing directives in the text provided
as arguments for a macro. That case is undefined in the C standard. but
in GNU C conditional directives in macro arguments are clear and valid.

A paradoxical case is to redefine a macro within the call to that same
macro. What happens is, the new definition takes effect in time for
pre-expansion of *all* the arguments, then the original definition is
expanded to replace the call. Here is a pathological example:

``` C
#define f(x) x x
f (first f second
#undef f
#define f 2
f)
```

which expands to

``` C
first 2 second 2 first 2 second 2
```

with the semantics described above. We suggest you avoid writing code
which does this sort of thing.
