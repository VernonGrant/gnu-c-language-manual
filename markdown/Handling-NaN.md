Next: [Signed Zeros](Signed-Zeros.md), Previous: [Handling
Infinity](Handling-Infinity.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 28.14 Handling NaN 


NaNs are not numbers: they represent values from computations that
produce undefined results. They have a distinctive property that makes
them unlike any other floating-point value: they are *unequal to
everything, including themselves*! Thus, you can write a test for a NaN
like this:

``` C
if (x != x)
  printf ("x is a NaN\n");
```

This test works in GNU C, but some compilers might evaluate that test
expression as false without properly checking for the NaN value. A more
portable way to test for NaN is to use the `isnan` function declared in
`math.h`:

``` C
if (isnan (x))
  printf ("x is a NaN\n");
```

See [Floating Point
Classes](https://www.gnu.org/software/libc/manual/html_node/Floating-Point-Classes.md#Floating-Point-Classes)
in The GNU C Library Reference Manual.

One important use of NaNs is marking of missing data. For example, in
statistics, such data must be omitted from computations. Use of any
particular finite value for missing data would eventually collide with
real data, whereas such data could never be a NaN, so it is an ideal
marker. Functions that deal with collections of data that may have holes
can be written to test for, and ignore, NaN values.

It is easy to generate a NaN in computations: evaluating `0.0 / 0.0` is
the commonest way, but `Infinity - Infinity`, `Infinity / Infinity`, and
`sqrt (-1.0)` also work. Functions that receive out-of-bounds arguments
can choose to return a stored NaN value, such as with the `NAN` macro
defined in `math.h`, but that does not set the *invalid operand*
exception flag, and that can fool some programs.


Like Infinity, NaNs propagate in computations, but they are even
stickier, because they never disappear in division. Thus, once a NaN
appears in a chain of numerical operations, it is almost certain to pop
out into the final results. The programmer has to decide whether that is
expected, or whether there is a coding or algorithmic error that needs
repair.

In general, when function gets a NaN argument, it usually returns a NaN.
However, there are some exceptions in the math-library functions that
you need to be aware of, because they violate the
*NaNs-always-propagate* rule:

-   `pow (x, 0.0)` always returns `1.0`, even if `x` is 0.0, Infinity,
    or a NaN.
-   `pow (1, y)` always returns `1`, even if `y` is a NaN.
-   `hypot (INFINITY, y)` and `hypot (-INFINITY, y)` both always return
    `INFINITY`, even if `y` is a Nan.
-   If just one of the arguments to `fmax (x, y)` or `fmin (x, y)` is a
    NaN, it returns the other argument. If both arguments are NaNs, it
    returns a NaN, but there is no requirement about where it comes
    from: it could be `x`, or `y`, or some other quiet NaN.

NaNs are also used for the return values of math-library functions where
the result is not representable in real arithmetic, or is mathematically
undefined or uncertain, such as `sqrt (-1.0)` and `sin (Infinity)`.
However, note that a result that is merely too big to represent should
always produce an Infinity, such as with `exp (1000.0)` (too big) and
`exp (Infinity)` (truly infinite).

------------------------------------------------------------------------

Next: [Signed Zeros](Signed-Zeros.md), Previous: [Handling
Infinity](Handling-Infinity.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
