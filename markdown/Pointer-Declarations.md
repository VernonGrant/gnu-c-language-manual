Next: [Pointer-Type Designators](Pointer-Type-Designators.md),
Previous: [Pointer Types](Pointer-Types.md), Up:
[Pointers](Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 14.3 Pointer-Variable Declarations 

The way to declare that a variable `foo` points to type `t`{.variable}
is

``` C
t *foo;
```

To remember this syntax, think "if you dereference `foo`, using the
'`*`' operator, what you get is type `t`{.variable}. Thus,
`foo` points to type `t`{.variable}."

Thus, we can declare variables that hold pointers to these three types,
like this:

``` C
int *ptri;            /* Pointer to int. */
double *ptrd;         /* Pointer to double. */
double (*ptrda)[5];   /* Pointer to double[5]. */
```

'`int *ptri;`' means, "if you dereference `ptri`, you get an
`int`." '`double (*ptrda)[5];`' means, "if you dereference
`ptrda`, then subscript it by an integer less than 5, you get a
`double`." The parentheses express the point that you would dereference
it first, then subscript it.

Contrast the last one with this:

``` C
double *aptrd[5];     /* Array of five pointers to double. */
```

Because '`*`' has higher syntactic precedence than
subscripting, you would subscript `aptrd` then dereference it.
Therefore, it declares an array of pointers, not a pointer.
