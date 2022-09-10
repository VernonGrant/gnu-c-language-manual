Next: [Clean Use of the Comma Operator](Clean-Comma.md), Up: [Comma
Operator](Comma-Operator.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 8.5.1 The Uses of the Comma Operator 

With commas, you can put several expressions into a place that requires
just one expression---for example, in the header of a `for` statement.
This statement

``` C
for (i = 0, j = 10, k = 20; i < n; i++)
```

contains three assignment expressions, to initialize `i`, `j` and `k`.
The syntax of `for` requires just one expression for initialization; to
include three assignments, we use commas to bundle them into a single
larger expression, `i = 0, j = 10, k = 20`. This technique is also
useful in the loop-advance expression, the last of the three inside the
`for` parentheses.

In the `for` statement and the `while` statement (see [Loop
Statements](Loop-Statements.md)), a comma provides a way to perform
some side effect before the loop-exit test. For example,

``` C
while (printf ("At the test, x = %d\n", x), x != 0)
```
