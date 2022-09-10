Next: [Floating Arithmetic Exception Flags](Exception-Flags.md),
Previous: [Special Floating-Point Values](Special-Float-Values.md),
Up: [Floating Point in Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 28.4 Invalid Optimizations 


Signed zeros, Infinity, and NaN invalidate some optimizations by
programmers and compilers that might otherwise have seemed obvious:

-   `x + 0` and `x - 0` are not the same as `x` when `x` is zero,
    because the result depends on the rounding rule. See
    [Rounding](Rounding.md), for more about rounding rules.
-   `x * 0.0` is not the same as `0.0` when `x` is Infinity, a NaN, or
    negative zero.
-   `x / x` is not the same as `1.0` when `x` is Infinity, a NaN, or
    zero.
-   `(x - y)` is not the same as `-(y - x)` because when the operands
    are finite and equal, one evaluates to `+0` and the other to `-0`.
-   `x - x` is not the same as `0.0` when `x`{.variable} is Infinity or
    a NaN.
-   `x == x` and `x != x` are not equivalent to `1` and `0` when
    `x`{.variable} is a NaN.
-   `x < y` and `isless (x, y)` are not equivalent, because the first
    sets a sticky exception flag (see [Floating Arithmetic Exception
    Flags](Exception-Flags.md)) when an operand is a NaN, whereas the
    second does not affect that flag. The same holds for the other
    `isxxx` functions that are companions to relational operators. See
    [FP Comparison
    Functions](https://www.gnu.org/software/libc/manual/html_node/FP-Comparison-Functions.md#FP-Comparison-Functions)
    in The GNU C Library Reference Manual.

The `-funsafe-math-optimizations` option enables these
optimizations.
