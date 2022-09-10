Next: [Handling NaN](Handling-NaN.md), Previous: [Exact Floating-Point
Constants](Exact-Floating-Constants.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 28.13 Handling Infinity 


As we noted earlier, the IEEE 754 model of computing is not to stop the
program when exceptional conditions occur. It takes note of exceptional
values or conditions by setting sticky *exception flags*, or by
producing results with the special values Infinity and QNaN. In this
section, we discuss Infinity; see [Handling NaN](Handling-NaN.md) for
the other.

In GNU C, you can create a value of negative Infinity in software like
this:

``` verbatim
double x;

x = -1.0 / 0.0;
```

GNU C supplies the `__builtin_inf`, `__builtin_inff`, and
`__builtin_infl` macros, and the GNU C Library provides the `INFINITY`
macro, all of which are compile-time constants for positive infinity.

GNU C also provides a standard function to test for an Infinity:
`isinf (x)` returns `1` if the argument is a signed infinity, and `0` if
not.

Infinities can be compared, and all Infinities of the same sign are
equal: there is no notion in IEEE 754 arithmetic of different kinds of
Infinities, as there are in some areas of mathematics. Positive Infinity
is larger than any finite value, and negative Infinity is smaller than
finite value.

Infinities propagate in addition, subtraction, multiplication, and
square root, but in division, they disappear, because of the rule that
`finite / Infinity` is `0.0`. Thus, an overflow in an intermediate
computation that produces an Infinity is likely to be noticed later in
the final results. The programmer can then decide whether the overflow
is expected, and acceptable, or whether the code possibly has a bug, or
needs to be run in higher precision, or redesigned to avoid the
production of the Infinity.

------------------------------------------------------------------------

Next: [Handling NaN](Handling-NaN.md), Previous: [Exact Floating-Point
Constants](Exact-Floating-Constants.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
