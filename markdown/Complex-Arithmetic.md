Next: [Round-Trip Base Conversion](Round_002dTrip-Base-Conversion.md),
Previous: [Machine Epsilon](Machine-Epsilon.md), Up: [Floating Point
in Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 28.19 Complex Arithmetic 


We've already looked at defining and referring to complex numbers (see
[Complex Data Types](Complex-Data-Types.md)). What is important to
discuss here are some issues that are unlikely to be obvious to
programmers without extensive experience in both numerical computing,
and in complex arithmetic in mathematics.

The first important point is that, unlike real arithmetic, in complex
arithmetic, the danger of significance loss is *pervasive*, and affects
*every one* of the basic operations, and *almost all* of the
math-library functions. To understand why, recall the rules for complex
multiplication and division:

``` C
a = u + I*v              /* First operand. */
b = x + I*y              /* Second operand. */

prod = a * b
     = (u + I*v) * (x + I*y)
     = (u * x - v * y) + I*(v * x + u * y)

quo  = a / b
     = (u + I*v) / (x + I*y)
     = [(u + I*v) * (x - I*y)] / [(x + I*y) * (x - I*y)]
     = [(u * x + v * y) + I*(v * x - u * y)] / (x**2 + y**2)
```

There are four critical observations about those formulas:

-   the multiplications on the right-hand side introduce the possibility
    of premature underflow or overflow;
-   the products must be accurate to twice working precision;
-   there is *always* one subtraction on the right-hand sides that is
    subject to catastrophic significance loss; and
-   complex multiplication has up to *six* rounding errors, and complex
    division has *ten* rounding errors.


Another point that needs careful study is the fact that many functions
in complex arithmetic have *branch cuts*. You can view a function with a
complex argument, `f (z)`, as `f (x + I*y)`, and thus, it defines a
relation between a point `(x, y)` on the complex plane with an elevation
value on a surface. A branch cut looks like a tear in that surface, so
approaching the cut from one side produces a particular value, and from
the other side, a quite different value. Great care is needed to handle
branch cuts properly, and even small numerical errors can push a result
from one side to the other, radically changing the returned value. As we
reported earlier, correct handling of the sign of zero is critically
important for computing near branch cuts.

The best advice that we can give to programmers who need complex
arithmetic is to always use the *highest precision available*, and then
to carefully check the results of test calculations to gauge the likely
accuracy of the computed results. It is easy to supply test values of
real and imaginary parts where all five basic operations in complex
arithmetic, and almost all of the complex math functions, lose *all*
significance, and fail to produce even a single correct digit.

Even though complex arithmetic makes some programming tasks easier, it
may be numerically preferable to rework the algorithm so that it can be
carried out in real arithmetic. That is commonly possible in matrix
algebra.

GNU C can perform code optimization on complex number multiplication and
division if certain boundary checks will not be needed. The command-line
option `-fcx-limited-range` tells the compiler that a range
reduction step is not needed when performing complex division, and that
there is no need to check if a complex multiplication or division
results in the value `Nan + I*NaN`. By default these checks are enabled.
You can explicitly enable them with the `-fno-cx-limited-range`
option.

------------------------------------------------------------------------

Next: [Round-Trip Base Conversion](Round_002dTrip-Base-Conversion.md),
Previous: [Machine Epsilon](Machine-Epsilon.md), Up: [Floating Point
in Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
