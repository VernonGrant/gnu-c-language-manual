Next: [Rounding](Rounding.md), Previous: [Floating Arithmetic
Exception Flags](Exception-Flags.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 28.6 Exact Floating-Point Arithmetic 


As long as the numbers are exactly representable (fractions whose
denominator is a power of 2), and intermediate results do not require
rounding, then floating-point arithmetic is *exact*. It is easy to
predict how many digits are needed for the results of arithmetic
operations:

-   addition and subtraction of two `n`-digit values with the
    *same* exponent require at most `n + 1` digits, but when the
    exponents differ, many more digits may be needed;
-   multiplication of two `n`-digit values requires exactly 2
    `n` digits;
-   although integer division produces a quotient and a remainder of no
    more than `n`-digits, floating-point remainder and square
    root may require an unbounded number of digits, and the quotient can
    need many more digits than can be stored.

Whenever a result requires more than `n` digits, rounding is
needed.
