Next: [Write Assignments in Separate
Statements](Write-Assignments-Separately.md), Previous: [Postincrement
and Postdecrement](Postincrement_002fPostdecrement.md), Up:
[Assignment Expressions](Assignment-Expressions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 7.6 Pitfall: Assignment in Subexpressions 


In C, the order of computing parts of an expression is not fixed. Aside
from a few special cases, the operations can be computed in any order.
If one part of the expression has an assignment to `x` and another part
of the expression uses `x`, the result is unpredictable because that use
might be computed before or after the assignment.

Here's an example of ambiguous code:

``` C
x = 20;
printf ("%d %d\n", x, x = 4);
```

If the second argument, `x`, is computed before the third argument,
`x = 4`, the second argument's value will be 20. If they are computed in
the other order, the second argument's value will be 4.

Here's one way to make that code unambiguous:

``` C
y = 20;
printf ("%d %d\n", y, x = 4);
```

Here's another way, with the other meaning:

``` C
x = 4;
printf ("%d %d\n", x, x);
```

This issue applies to all kinds of assignments, and to the increment and
decrement operators, which are equivalent to assignments. See [Order of
Execution](Order-of-Execution.md), for more information about this.

However, it can be useful to write assignments inside an `if`-condition
or `while`-test along with logical operators. See [Logical Operators and
Assignments](Logicals-and-Assignments.md).
