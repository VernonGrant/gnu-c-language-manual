Next: [Shift Operations](Shift-Operations.md), Previous: [Division and
Remainder](Division-and-Remainder.md), Up:
[Arithmetic](Arithmetic.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 6.6 Numeric Comparisons 


There are two kinds of comparison operators: *equality* and *ordering*.
Equality comparisons test whether two expressions have the same value.
The result is a *truth value*: a number that is 1 for "true" and 0 for
"false."

``` C
a == b   /* Test for equal.  */
a != b   /* Test for not equal.  */
```

The equality comparison is written `==` because plain `=` is the
assignment operator.

Ordering comparisons test which operand is greater or less. Their
results are truth values. These are the ordering comparisons of C:

``` C
a < b   /* Test for less-than.  */
a > b   /* Test for greater-than.  */
a <= b  /* Test for less-than-or-equal.  */
a >= b  /* Test for greater-than-or-equal.  */
```

For any integers `a` and `b`, exactly one of the comparisons `a < b`,
`a == b` and `a > b` is true, just as in mathematics. However, if `a`
and `b` are special floating point values (not ordinary numbers), all
three can be false. See [Special Floating-Point
Values](Special-Float-Values.md), and [Invalid
Optimizations](Invalid-Optimizations.md).
