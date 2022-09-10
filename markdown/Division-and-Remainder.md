Next: [Numeric Comparisons](Numeric-Comparisons.md), Previous:
[Mixed-Mode Arithmetic](Mixed-Mode.md), Up:
[Arithmetic](Arithmetic.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 6.5 Division and Remainder 


Division of integers in C rounds the result to an integer. The result is
always rounded towards zero.

``` C
 16 / 3  ⇒ 5
-16 / 3  ⇒ -5
 16 / -3 ⇒ -5
-16 / -3 ⇒ 5
```

To get the corresponding remainder, use the '`%`' operator:

``` C
 16 % 3  ⇒ 1
-16 % 3  ⇒ -1
 16 % -3 ⇒ 1
-16 % -3 ⇒ -1
```

'`%`' has the same operator precedence as '`/`' and
'`*`'.

From the rounded quotient and the remainder, you can reconstruct the
dividend, like this:

``` C
int
original_dividend (int divisor, int quotient, int remainder)
{
  return divisor * quotient + remainder;
}
```

To do unrounded division, use floating point. If only one operand is
floating point, '`/`' converts the other operand to floating
point.

``` C
16.0 / 3   ⇒ 5.333333333333333
16   / 3.0 ⇒ 5.333333333333333
16.0 / 3.0 ⇒ 5.333333333333333
16   / 3   ⇒ 5
```

The remainder operator '`%`' is not allowed for floating-point
operands, because it is not needed. The concept of remainder makes sense
for integers because the result of division of integers has to be an
integer. For floating point, the result of division is a floating-point
number, in other words a fraction, which will differ from the exact
result only by a very small amount.

There are functions in the standard C library to calculate remainders
from integral-values division of floating-point numbers. See [The GNU C
Library](https://www.gnu.org/software/libc/manual/html_node/Remainder-Functions.md#Remainder-Functions)
in The GNU C Library Reference Manual.

Integer division overflows in one specific case: dividing the smallest
negative value for the data type (see [Maximum and Minimum
Values](Maximum-and-Minimum-Values.md)) by -1. That's because the
correct result, which is the corresponding positive number, does not fit
(see [Integer Overflow](Integer-Overflow.md)) in the same number of
bits. On some computers now in use, this always causes a signal `SIGFPE`
(see [Signals](Signals.md)), the same behavior that the option
`-ftrapv` specifies (see [Overflow with Signed
Integers](Signed-Overflow.md)).

Division by zero leads to unpredictable results---depending on the type
of computer, it might cause a signal `SIGFPE`, or it might produce a
numeric result.


**Watch out:** Make sure the program does not divide by zero. If you
can't prove that the divisor is not zero, test whether it is zero, and
skip the division if so.

------------------------------------------------------------------------

Next: [Numeric Comparisons](Numeric-Comparisons.md), Previous:
[Mixed-Mode Arithmetic](Mixed-Mode.md), Up:
[Arithmetic](Arithmetic.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
