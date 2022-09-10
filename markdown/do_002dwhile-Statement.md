Next: [`break` Statement](break-Statement.md), Previous: [`while`
Statement](while-Statement.md), Up: [Loop
Statements](Loop-Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 19.6.2 `do-while` Statement 


The `do`--`while` statement is a simple loop construct that performs the
test at the end of the iteration.

``` C
do
  body
while (test);
```

Here, `body` is a statement (possibly a block) to repeat, and
`test` is an expression that controls whether to repeat it
again.

Each iteration of the loop starts by executing `body`. Then
it computes `test` and, if it is true (nonzero), that means
to go back and start over with `body`. If `test`
is false (zero), then the loop stops repeating and execution moves on
past it.
