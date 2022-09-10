Next: [Rounding Control](Rounding-Control.md), Previous: [Signed
Zeros](Signed-Zeros.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 28.16 Scaling by Powers of the Base 


We have discussed rounding errors several times in this chapter, but it
is important to remember that when results require no more bits than the
exponent and significand bits can represent, those results are *exact*.

One particularly useful exact operation is scaling by a power of the
base. While one, in principle, could do that with code like this:

``` C
y = x * pow (2.0, (double)k);   /* Undesirable scaling: avoid! */
```

that is not advisable, because it relies on the quality of the
math-library power function, and that happens to be one of the most
difficult functions in the C math library to make accurate. What is
likely to happen on many systems is that the returned value from `pow`
will be close to a power of two, but slightly different, so the
subsequent multiplication introduces rounding error.

The correct, and fastest, way to do the scaling is either via the
traditional C library function, or with its C99 equivalent:

``` C
y = ldexp (x, k);            /* Traditional pre-C99 style. */
y = scalbn (x, k);           /* C99 style. */
```

Both functions return `x * 2**k`. See [Normalization
Functions](https://www.gnu.org/software/libc/manual/html_node/Normalization-Functions.md#Normalization-Functions)
in The GNU C Library Reference Manual.
