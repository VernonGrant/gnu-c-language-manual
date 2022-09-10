Next: [Statements and Declarations in
Expressions](Statement-Exprs.md), Previous: [Locally Declared
Labels](Local-Labels.md), Up: [Statements](Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 19.14 Labels as Values 


In GNU C, you can get the address of a label defined in the current
function (or a local label defined in the containing function) with the
unary operator '`&&`'. The value has type `void *`. This value
is a constant and can be used wherever a constant of that type is valid.
For example:

``` C
void *ptr;
…
ptr = &&foo;
```

To use these values requires a way to jump to one. This is done with the
computed goto statement[^5^](#FOOT5), `goto *exp;`. For example,

``` C
goto *ptr;
```

Any expression of type `void *` is allowed.

See [`goto` Statement and Labels](goto-Statement.md).

-   [Label Value Uses](Label-Value-Uses.md)
-   [Label Value Caveats](Label-Value-Caveats.md)


------------------------------------------------------------------------

#### Footnotes 

##### [(5)](#DOCF5)

The analogous feature in Fortran is called an assigned goto, but that
name seems inappropriate in C, since you can do more with label
addresses than store them in special label variables.
