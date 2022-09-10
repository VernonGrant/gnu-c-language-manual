Next: [Rounding Issues](Rounding-Issues.md), Previous: [Exact
Floating-Point Arithmetic](Exact-Floating_002dPoint.md), Up: [Floating
Point in Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 28.7 Rounding 


When floating-point arithmetic produces a result that can't fit exactly
in the significand of the type that's in use, it has to *round* the
value. The basic arithmetic operations---addition, subtraction,
multiplication, division, and square root---always produce a result that
is equivalent to the exact, possibly infinite-precision result rounded
to storage precision according to the current rounding rule.

Rounding sets the `FE_INEXACT` exception flag (see [Floating Arithmetic
Exception Flags](Exception-Flags.md)). This enables programs to
determine that rounding has occurred.

Rounding consists of adjusting the exponent to bring the significand
back to the required base-point alignment, then applying the current
*rounding rule* to squeeze the significand into the fixed available
size.

The current rule is selected at run time from four options. Here they
are:

-   \* *round-to-nearest*, with ties rounded to an even integer;
-   \* *round-up*, towards `+Infinity`;
-   \* *round-down*, towards `-Infinity`;
-   \* *round-towards-zero*.

Under those four rounding rules, a decimal value `-1.2345` that is to be
rounded to a four-digit result would become `-1.234`, `-1.234`,
`-1.235`, and `-1.234`, respectively.

The default rounding rule is *round-to-nearest*, because that has the
least bias, and produces the lowest average error. When the true result
lies exactly halfway between two representable machine numbers, the
result is rounded to the one that ends with an even digit.

The *round-towards-zero* rule was common on many early computer designs,
because it is the easiest to implement: it just requires silent
truncation of all extra bits.

The two other rules, *round-up* and *round-down*, are essential for
implementing *interval arithmetic*, whereby each arithmetic operation
produces lower and upper bounds that are guaranteed to enclose the exact
result.

See [Rounding Control](Rounding-Control.md), for details on getting
and setting the current rounding mode.

------------------------------------------------------------------------

Next: [Rounding Issues](Rounding-Issues.md), Previous: [Exact
Floating-Point Arithmetic](Exact-Floating_002dPoint.md), Up: [Floating
Point in Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
