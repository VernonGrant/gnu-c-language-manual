Next: [Operator Precedence Problems](Operator-Precedence-Problems.md),
Up: [Macro Pitfalls](Macro-Pitfalls.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.5.10.1 Misnesting 

When a macro is called with arguments, the arguments are substituted
into the macro body and the result is checked, together with the rest of
the input file, for more macro calls. It is possible to piece together a
macro call coming partially from the macro body and partially from the
arguments. For example,

``` C
#define twice(x) (2*(x))
#define call_with_1(x) x(1)
call_with_1 (twice)
     → twice(1)
     → (2*(1))
```

Macro definitions do not have to have balanced parentheses. By writing
an unbalanced open parenthesis in a macro body, it is possible to create
a macro call that begins inside the macro body but ends outside of it.
For example,

``` C
#define strange(file) fprintf (file, "%s %d",
/* … */
strange(stderr) p, 35)
     → fprintf (stderr, "%s %d", p, 35)
```

The ability to piece together a macro call can be useful, but the use of
unbalanced open parentheses in a macro body is just confusing, and
should be avoided.
