Next: [Logical Operators and
Assignments](Logicals-and-Assignments.md), Previous: [Logical
Operators](Logical-Operators.md), Up: [Execution Control
Expressions](Execution-Control-Expressions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 8.2 Logical Operators and Comparisons 

The most common thing to use inside the logical operators is a
comparison. Conveniently, '`&&`' and '`||`' have lower
precedence than comparison operators and arithmetic operators, so we can
write expressions like this without parentheses and get the nesting that
is natural: two comparison operations that must both be true.

``` C
if (r != 0 && x % r == 0)
```

This example also shows how it is useful that '`&&`' guarantees
to skip the right operand if the left one turns out false. Because of
that, this code never tries to divide by zero.

This is equivalent:

``` C
if (r && x % r == 0)
```

A truth value is simply a number, so using `r` as a truth value tests
whether it is nonzero. But `r`'s meaning as en expression is not a truth
value---it is a number to divide by. So it is better style to write the
explicit `!= 0`.

Here's another equivalent way to write it:

``` C
if (!(r == 0) && x % r == 0)
```

This illustrates the unary '`!`' operator, and the need to
write parentheses around its operand.
