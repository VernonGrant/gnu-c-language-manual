Next: [Blocks](Blocks.md), Previous: [`if`
Statement](if-Statement.md), Up: [Statements](Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 19.3 `if-else` Statement 


An `if`-`else` statement computes an expression to decide which of two
nested statements to execute. It looks like this:

``` C
if (condition)
  if-true-substatement
else
  if-false-substatement
```

The first thing this does is compute the value of
`condition`{.variable}. If that is true (nonzero), then it executes the
statement `if-true-substatement`{.variable}. If the value of
`condition`{.variable} is false (zero), then it executes the statement
`if-false-substatement`{.variable} instead.

This is a *complex statement* because it contains components
`if-true-substatement`{.variable} and `if-else-substatement`{.variable}
that are nested statements. Each must be one and only one statement. The
way to put multiple statements in such a component is to group them into
a *block* (see [Blocks](Blocks.md)).
