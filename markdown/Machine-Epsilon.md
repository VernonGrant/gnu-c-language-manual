Next: [Complex Arithmetic](Complex-Arithmetic.md), Previous: [Rounding
Control](Rounding-Control.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 28.18 Machine Epsilon 


In any floating-point system, three attributes are particularly
important to know: *base* (the number that the exponent specifies a
power of), *precision* (number of digits in the significand), and
*range* (difference between most positive and most negative values). The
allocation of bits between exponent and significand decides the answers
to those questions.

A measure of the precision is the answer to the question: what is the
smallest number that can be added to `1.0` such that the sum differs
from `1.0`? That number is called the *machine epsilon*.

We could define the needed machine-epsilon constants for `float`,
`double`, and `long double` like this:

``` C
static const float  epsf = 0x1p-23;  /* about 1.192e-07 */
static const double eps  = 0x1p-52;  /* about 2.220e-16 */
static const long double epsl = 0x1p-63;  /* about 1.084e-19 */
```

Instead of the hexadecimal constants, we could also have used the
Standard C macros, `FLT_EPSILON`, `DBL_EPSILON`, and `LDBL_EPSILON`.

It is useful to be able to compute the machine epsilons at run time, and
we can easily generalize the operation by replacing the constant `1.0`
with a user-supplied value:

``` C
double
macheps (double x)
{ /* Return machine epsilon for x,  */
   /* such that x + macheps (x) > x.  */
  static const double base = 2.0;
  double eps;

  if (isnan (x))
      eps = x;
  else
    {
      eps = (x == 0.0) ? 1.0 : x;

      while ((x + eps / base) != x)
          eps /= base;          /* Always exact!  */
    }

  return (eps);
}
```

If we call that function with arguments from `0` to `10`, as well as
Infinity and NaN, and print the returned values in hexadecimal, we get
output like this:

``` C
macheps (  0) = 0x1.0000000000000p-1074
macheps (  1) = 0x1.0000000000000p-52
macheps (  2) = 0x1.0000000000000p-51
macheps (  3) = 0x1.8000000000000p-52
macheps (  4) = 0x1.0000000000000p-50
macheps (  5) = 0x1.4000000000000p-51
macheps (  6) = 0x1.8000000000000p-51
macheps (  7) = 0x1.c000000000000p-51
macheps (  8) = 0x1.0000000000000p-49
macheps (  9) = 0x1.2000000000000p-50
macheps ( 10) = 0x1.4000000000000p-50
macheps (Inf) = infinity
macheps (NaN) = nan
```

Notice that `macheps` has a special test for a NaN to prevent an
infinite loop.

Our code made another test for a zero argument to avoid getting a zero
return. The returned value in that case is the smallest representable
floating-point number, here the subnormal value `2**(-1074)`, which is
about `4.941e-324`.

No special test is needed for an Infinity, because the `eps`-reduction
loop then terminates at the first iteration.

Our `macheps` function here assumes binary floating point; some
architectures may differ.

The C library includes some related functions that can also be used to
determine machine epsilons at run time:

``` C
#include <math.h>           /* Include for these prototypes. */

double      nextafter  (double x, double y);
float       nextafterf (float x, float y);
long double nextafterl (long double x, long double y);
```

These return the machine number nearest `x` in the direction
of `y`. For example, `nextafter (1.0, 2.0)` produces the same
result as `1.0 + macheps (1.0)` and `1.0 + DBL_EPSILON`. See [FP Bit
Twiddling](https://www.gnu.org/software/libc/manual/html_node/FP-Bit-Twiddling.md#FP-Bit-Twiddling)
in The GNU C Library Reference Manual.

It is important to know that the machine epsilon is not symmetric about
all numbers. At the boundaries where normalization changes the exponent,
the epsilon below `x` is smaller than that just above
`x` by a factor `1 / base`. For example, `macheps (1.0)`
returns `+0x1p-52`, whereas `macheps (-1.0)` returns `+0x1p-53`. Some
authors distinguish those cases by calling them the *positive* and
*negative*, or *big* and *small*, machine epsilons. You can produce
their values like this:

``` C
eps_neg = 1.0 - nextafter (1.0, -1.0);
eps_pos = nextafter (1.0, +2.0) - 1.0;
```

If `x` is a variable, such that you do not know its value at
compile time, then you can substitute literal `y` values with
either `-inf()` or `+inf()`, like this:

``` C
eps_neg = x - nextafter (x, -inf ());
eps_pos = nextafter (x, +inf() - x);
```

In such cases, if `x` is Infinity, then *the `nextafter`
functions return `y` if `x` equals
`y`*. Our two assignments then produce
`+0x1.fffffffffffffp+1023` (that is a hexadecimal floating point
constant and its value is around 1.798e+308; see [Floating-Point
Constants](Floating-Constants.md)) for `eps_neg`, and
Infinity for `eps_pos`. Thus, the call
`nextafter (INFINITY, -INFINITY)` can be used to find the largest
representable finite number, and with the call `nextafter (0.0, 1.0)`,
the smallest representable number (here, `0x1p-1074` (about 4.491e-324),
a number that we saw before as the output from `macheps (0.0)`).

------------------------------------------------------------------------

Next: [Complex Arithmetic](Complex-Arithmetic.md), Previous: [Rounding
Control](Rounding-Control.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
