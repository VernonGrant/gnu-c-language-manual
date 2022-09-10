Next: [`continue` Statement](continue-Statement.md), Previous:
[Omitted `for`-Expressions](Omitted-for_002dExpressions.md), Up: [Loop
Statements](Loop-Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 19.6.7 `for`-Index Declarations 

You can declare loop-index variables directly in the `start`{.variable}
portion of the `for`-loop, like this:

``` C
for (int i = 0; i < n; ++i)
  {
    …
  }
```

This kind of `start`{.variable} is limited to a single declaration; it
can declare one or more variables, separated by commas, all of which are
the same `basetype`{.variable} (`int`, in this example):

``` C
for (int i = 0, j = 1, *p = NULL; i < n; ++i, ++j, ++p)
  {
    …
  }
```

The scope of these variables is the `for` statement as a whole. See
[Variable Declarations](Variable-Declarations.md) for a explanation of
`basetype`{.variable}.

Variables declared in `for` statements should have initializers.
Omitting the initialization gives the variables unpredictable initial
values, so this code is erroneous.

``` C
for (int i; i < n; ++i)
  {
    …
  }
```
