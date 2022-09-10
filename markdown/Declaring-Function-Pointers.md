Next: [Assigning Function Pointers](Assigning-Function-Pointers.md),
Up: [Function Pointers](Function-Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 22.5.1 Declaring Function Pointers 


The declaration of a function pointer variable (or structure field)
looks almost like a function declaration, except it has an additional
'`*`' just before the variable name. Proper nesting requires a
pair of parentheses around the two of them. For instance, `int (*a) ();`
says, "Declare `a` as a pointer such that `*a` is an `int`-returning
function."

Contrast these three declarations:

``` C
/* Declare a function returning char *.  */
char *a (char *);
/* Declare a pointer to a function returning char.  */
char (*a) (char *);
/* Declare a pointer to a function returning char *.  */
char *(*a) (char *);
```

The possible argument types of the function pointed to are the same as
in a function declaration. You can write a prototype that specifies all
the argument types:

``` C
rettype (*function) (arguments…);
```

or one that specifies some and leaves the rest unspecified:

``` C
rettype (*function) (arguments…, ...);
```

or one that says there are no arguments:

``` C
rettype (*function) (void);
```

You can also write a non-prototype declaration that says nothing about
the argument types:

``` C
rettype (*function) ();
```

For example, here's a declaration for a variable that should point to
some arithmetic function that operates on two `double`s:

``` C
double (*binary_op) (double, double);
```

Structure fields, union alternatives, and array elements can be function
pointers; so can parameter variables. The function pointer declaration
construct can also be combined with other operators allowed in
declarations. For instance,

``` C
int **(*foo)();
```

declares `foo` as a pointer to a function that returns type `int **`,
and

``` C
int **(*foo[30])();
```

declares `foo` as an array of 30 pointers to functions that return type
`int **`.

``` C
int **(**foo)();
```

declares `foo` as a pointer to a pointer to a function that returns type
`int **`.

------------------------------------------------------------------------

Next: [Assigning Function Pointers](Assigning-Function-Pointers.md),
Up: [Function Pointers](Function-Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
