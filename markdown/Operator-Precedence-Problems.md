Next: [Swallowing the Semicolon](Swallowing-the-Semicolon.md),
Previous: [Misnesting](Misnesting.md), Up: [Macro
Pitfalls](Macro-Pitfalls.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.5.10.2 Operator Precedence Problems 


You may have noticed that in most of the macro definition examples shown
above, each occurrence of a macro parameter name had parentheses around
it. In addition, another pair of parentheses usually surrounds the
entire macro definition. Here is why it is best to write macros that
way.

Suppose you define a macro as follows,

``` C
#define ceil_div(x, y) (x + y - 1) / y
```

whose purpose is to divide, rounding up. (One use for this operation is
to compute how many `int` objects are needed to hold a certain number of
`char` objects.) Then suppose it is used as follows:

``` C
a = ceil_div (b & c, sizeof (int));
     → a = (b & c + sizeof (int) - 1) / sizeof (int);
```

This does not do what is intended. The operator-precedence rules of C
make it equivalent to this:

``` C
a = (b & (c + sizeof (int) - 1)) / sizeof (int);
```

What we want is this:

``` C
a = ((b & c) + sizeof (int) - 1)) / sizeof (int);
```

Defining the macro as

``` C
#define ceil_div(x, y) ((x) + (y) - 1) / (y)
```

provides the desired result.

Unintended grouping can result in another way. Consider
`sizeof ceil_div(1, 2)`. That has the appearance of a C expression that
would compute the size of the type of `ceil_div (1, 2)`, but in fact it
means something very different. Here is what it expands to:

``` C
sizeof ((1) + (2) - 1) / (2)
```

This would take the size of an integer and divide it by two. The
precedence rules have put the division outside the `sizeof` when it was
intended to be inside.

Parentheses around the entire macro definition prevent such problems.
Here, then, is the recommended way to define `ceil_div`:

``` C
#define ceil_div(x, y) (((x) + (y) - 1) / (y))
```

------------------------------------------------------------------------

Next: [Swallowing the Semicolon](Swallowing-the-Semicolon.md),
Previous: [Misnesting](Misnesting.md), Up: [Macro
Pitfalls](Macro-Pitfalls.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
