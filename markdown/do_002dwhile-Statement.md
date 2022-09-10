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

Here, `body`{.variable} is a statement (possibly a block) to repeat, and
`test`{.variable} is an expression that controls whether to repeat it
again.

Each iteration of the loop starts by executing `body`{.variable}. Then
it computes `test`{.variable} and, if it is true (nonzero), that means
to go back and start over with `body`{.variable}. If `test`{.variable}
is false (zero), then the loop stops repeating and execution moves on
past it.
