Next: [Dereferencing Pointers](Pointer-Dereference.md), Previous:
[Pointer-Variable Declarations](Pointer-Declarations.md), Up:
[Pointers](Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 14.4 Pointer-Type Designators 

Every type in C has a designator; you make it by deleting the variable
name and the semicolon from a declaration (see [Type
Designators](Type-Designators.md)). Here are the designators for the
pointer types of the example declarations in the previous section:

``` C
int *           /* Pointer to int. */
double *        /* Pointer to double. */
double (*)[5]   /* Pointer to double[5]. */
```

Remember, to understand what type a designator stands for, imagine the
corresponding variable declaration with a variable name in it, and
figure out what type that variable would have. Thus, the type designator
`double (*)[5]` corresponds to the variable declaration
`double (*variable)[5]`. That deciares a pointer variable which, when
dereferenced, gives an array of 5 `double`s. So the type designator
means, "pointer to an array of 5 `double`s."
