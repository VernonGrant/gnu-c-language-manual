Next: [Pointer-Variable Declarations](Pointer-Declarations.md),
Previous: [Address of Data](Address-of-Data.md), Up:
[Pointers](Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 14.2 Pointer Types 

For each data type `t`, there is a type for pointers to type
`t`. For these variables,

``` C
int i;
double a[5];
```

-   `i` has type `int`; we say `&i` is a "pointer to `int`."
-   `a` has type `double[5]`; we say `&a` is a "pointer to arrays of
    five `double`s."
-   `a[3]` has type `double`; we say `&a[3]` is a "pointer to `double`."
