Next: [Division and Remainder](Division-and-Remainder.md), Previous:
[Integer Overflow](Integer-Overflow.md), Up:
[Arithmetic](Arithmetic.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 6.4 Mixed-Mode Arithmetic 

Mixing integers and floating-point numbers in a basic arithmetic
operation converts the integers automatically to floating point. In most
cases, this gives exactly the desired results. But sometimes it matters
precisely where the conversion occurs.

If `i` and `j` are integers, `(i + j) * 2.0` adds them as an integer,
then converts the sum to floating point for the multiplication. If the
addition causes an overflow, that is not equivalent to converting each
integer to floating point and then adding the two floating point
numbers. You can get the latter result by explicitly converting the
integers, as in `((double) i + (double) j) * 2.0`. See [Explicit Type
Conversion](Explicit-Type-Conversion.md).

Adding or multiplying several values, including some integers and some
floating point, performs the operations left to right. Thus,
`3.0 + i + j` converts `i` to floating point, then adds 3.0, then
converts `j` to floating point and adds that. You can specify a
different order using parentheses: `3.0 + (i + j)` adds `i` and `j`
first and then adds that sum (converted to floating point) to 3.0. In
this respect, C differs from other languages, such as Fortran.
