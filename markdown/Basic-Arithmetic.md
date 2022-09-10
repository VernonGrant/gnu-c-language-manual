Next: [Integer Arithmetic](Integer-Arithmetic.md), Up:
[Arithmetic](Arithmetic.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 6.1 Basic Arithmetic 


Basic arithmetic in C is done with the usual binary operators of
algebra: addition ('`+`'), subtraction ('`-`'),
multiplication ('`*`') and division ('`/`'). The unary
operator '`-`' is used to change the sign of a number. The
unary `+` operator also exists; it yields its operand unaltered.

'`/`' is the division operator, but dividing integers may not
give the result you expect. Its value is an integer, which is not equal
to the mathematical quotient when that is a fraction. Use '`%`'
to get the corresponding integer remainder when necessary. See [Division
and Remainder](Division-and-Remainder.md). Floating point division
yields value as close as possible to the mathematical quotient.

These operators use algebraic syntax with the usual algebraic precedence
rule (see [Binary Operator Grammar](Binary-Operator-Grammar.md)) that
multiplication and division are done before addition and subtraction,
but you can use parentheses to explicitly specify how the operators
nest. They are left-associative (see [Associativity and
Ordering](Associativity-and-Ordering.md)). Thus,

``` C
-a + b - c + d * e / f
```

is equivalent to

``` C
(((-a) + b) - c) + ((d * e) / f)
```
