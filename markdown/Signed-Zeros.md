Next: [Scaling by Powers of the Base](Scaling-by-the-Base.md),
Previous: [Handling NaN](Handling-NaN.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 28.15 Signed Zeros 


The sign of zero is significant, and important, because it records the
creation of a value that is too small to represent, but came from either
the negative axis, or from the positive axis. Such fine distinctions are
essential for proper handling of *branch cuts* in complex arithmetic
(see [Complex Arithmetic](Complex-Arithmetic.md)).

The key point about signed zeros is that in comparisons, their sign does
not matter: `0.0 == -0.0` must *always* evaluate to `1` (true). However,
they are not *the same number*, and `-0.0` in C code stands for a
negative zero.
