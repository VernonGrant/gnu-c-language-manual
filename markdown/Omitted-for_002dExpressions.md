Next: [`for`-Index Declarations](for_002dIndex-Declarations.md),
Previous: [Example of `for`](Example-of-for.md), Up: [Loop
Statements](Loop-Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 19.6.6 Omitted `for`-Expressions 

A fully-fleshed `for` statement contains all these parts,

``` C
for (start; continue-test; advance)
  body
```

but you can omit any of the three expressions inside the parentheses.
The parentheses and the two semicolons are required syntactically, but
the expressions between them may be missing. A missing expression means
this loop doesn't use that particular feature of the `for` statement.

Instead of using `start`{.variable}, you can do the loop preparation
before the `for` statement: the effect is the same. So we could have
written the beginning of the previous example this way:

``` C
int i = 0;
for (; i < n; ++i)
```

instead of this way:

``` C
int i;
for (i = 0; i < n; ++i)
```

Omitting `continue-test`{.variable} means the loop runs forever (or
until something else causes exit from it). Statements inside the loop
can test conditions for termination and use '`break;`' to exit.
This is more flexible since you can put those tests anywhere in the
loop, not solely at the beginning.

Putting an expression in `advance`{.variable} is almost equivalent to
writing it at the end of the loop body; it does almost the same thing.
The only difference is for the `continue` statement (see [`continue`
Statement](continue-Statement.md)). So we could have written this:

``` C
for (i = 0; i < n;)
  {
    …
    ++i;
  }
```

instead of this:

``` C
for (i = 0; i < n; ++i)
  {
    …
  }
```

The choice is mainly a matter of what is more readable for programmers.
However, there is also a syntactic difference: `advance`{.variable} is
an expression, not a statement. It can't include loops, blocks,
declarations, etc.

------------------------------------------------------------------------

Next: [`for`-Index Declarations](for_002dIndex-Declarations.md),
Previous: [Example of `for`](Example-of-for.md), Up: [Loop
Statements](Loop-Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
