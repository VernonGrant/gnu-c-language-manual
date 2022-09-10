Next: [Exact Floating-Point Constants](Exact-Floating-Constants.md),
Previous: [Fused Multiply-Add](Fused-Multiply_002dAdd.md), Up:
[Floating Point in Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 28.11 Error Recovery 


When two numbers are combined by one of the four basic operations, the
result often requires rounding to storage precision. For accurate
computation, one would like to be able to recover that rounding error.
With historical floating-point designs, it was difficult to do so
portably, but now that IEEE 754 arithmetic is almost universal, the job
is much easier.

For addition with the default *round-to-nearest* rounding mode, we can
determine the error in a sum like this:

``` C
volatile double err, sum, tmp, x, y;

if (fabs (x) >= fabs (y))
  {
    sum = x + y;
    tmp = sum - x;
    err = y - tmp;
  }
else /* fabs (x) < fabs (y) */
  {
    sum = x + y;
    tmp = sum - y;
    err = x - tmp;
  }
```

This basic operation, which has come to be called *twosum* in the
numerical-analysis literature, is the first key to tracking, and
accounting for, rounding error.

To determine the error in subtraction, just swap the `+` and `-`
operators.

We used the `volatile` qualifier (see [`volatile` Variables and
Fields](volatile.md)) in the declaration of the variables, which
forces the compiler to store and retrieve them from memory, and prevents
the compiler from optimizing `err = y - ((x + y) - x)` into `err = 0`.

For multiplication, we can compute the rounding error without magnitude
tests with the FMA operation (see [Fused
Multiply-Add](Fused-Multiply_002dAdd.md)), like this:

``` C
volatile double err, prod, x, y;
prod = x * y;                /* rounded product */
err  = fma (x, y, -prod);    /* exact product = prod + err */
```

For addition, subtraction, and multiplication, we can represent the
exact result with the notional sum of two values. However, the exact
result of division, remainder, or square root potentially requires an
infinite number of digits, so we can at best approximate it.
Nevertheless, we can compute an error term that is close to the true
error: it is just that error value, rounded to machine precision.

For division, you can approximate `x / y` with `quo + err` like this:

``` C
volatile double err, quo, x, y;
quo = x / y;
err = fma (-quo, y, x) / y;
```

For square root, we can approximate `sqrt (x)` with `root + err` like
this:

``` C
volatile double err, root, x;
root = sqrt (x);
err = fma (-root, root, x) / (root + root);
```

With the reliable and predictable floating-point design provided by IEEE
754 arithmetic, we now have the tools we need to track errors in the
five basic floating-point operations, and we can effectively simulate
computing in twice working precision, which is sometimes sufficient to
remove almost all traces of arithmetic errors.

------------------------------------------------------------------------

Next: [Exact Floating-Point Constants](Exact-Floating-Constants.md),
Previous: [Fused Multiply-Add](Fused-Multiply_002dAdd.md), Up:
[Floating Point in Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
