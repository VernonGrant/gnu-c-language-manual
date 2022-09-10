Next: [`if-else` Statement](if_002delse-Statement.md), Previous:
[Expression Statement](Expression-Statement.md), Up:
[Statements](Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 19.2 `if` Statement 


An `if` statement computes an expression to decide whether to execute
the following statement or not. It looks like this:

``` C
if (condition)
  execute-if-true
```

The first thing this does is compute the value of
`condition`. If that is true (nonzero), then it executes the
statement `execute-if-true`. If the value of
`condition` is false (zero), it doesn't execute
`execute-if-true`; instead, it does nothing.

This is a *complex statement* because it contains a component
`if-true-substatement` that is a nested statement. It must be
one and only one statement. The way to put multiple statements there is
to group them into a *block* (see [Blocks](Blocks.md)).
