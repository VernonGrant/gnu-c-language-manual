Next: [Example of `for`](Example-of-for.md), Previous: [`break`
Statement](break-Statement.md), Up: [Loop
Statements](Loop-Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 19.6.4 `for` Statement 


A `for` statement uses three expressions written inside a parenthetical
group to define the repetition of the loop. The first expression says
how to prepare to start the loop. The second says how to test, before
each iteration, whether to continue looping. The third says how to
advance, at the end of an iteration, for the next iteration. All
together, it looks like this:

``` C
for (start; continue-test; advance)
  body
```

The first thing the `for` statement does is compute `start`{.variable}.
The next thing it does is compute the expression
`continue-test`{.variable}. If that expression is false (zero), the
`for` statement finishes immediately, so `body`{.variable} is executed
zero times.

However, if `continue-test`{.variable} is true (nonzero), the `for`
statement executes `body`{.variable}, then `advance`{.variable}. Then it
loops back to the not-quite-top to test `continue-test`{.variable}
again. But it does not compute `start`{.variable} again.
