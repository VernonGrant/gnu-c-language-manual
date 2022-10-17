Next: [Machine Epsilon](Machine-Epsilon.md), Previous: [Scaling by
Powers of the Base](Scaling-by-the-Base.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 28.17 Rounding Control 


Here we describe how to specify the rounding mode at run time. System
header file `fenv.h` provides the prototypes for these
functions. See
[Rounding](https://www.gnu.org/software/libc/manual/html_node/Rounding.md#Rounding)
in The GNU C Library Reference Manual.

That header file also provides constant names for the four rounding
modes: `FE_DOWNWARD`, `FE_TONEAREST`, `FE_TOWARDZERO`, and `FE_UPWARD`.

The function `fegetround` examines and returns the current rounding
mode. On a platform with IEEE 754 floating point, the value will always
equal one of those four constants. On other platforms, it may return a
negative value. The function `fesetround` sets the current rounding
mode.

Changing the rounding mode can be slow, so it is useful to minimize the
number of changes. For interval arithmetic, we seem to need three
changes for each operation, but we really only need two, because we can
write code like this example for interval addition of two reals:

``` C
{
  struct interval_double
    {
      double hi, lo;
    } v;
  extern volatile double x, y;
  int rule;

  rule = fegetround ();

  if (fesetround (FE_UPWARD) == 0)
    {
      v.hi = x + y;
      v.lo = -(-x - y);
    }
  else
    fatal ("ERROR: failed to change rounding rule");

  if (fesetround (rule) != 0)
    fatal ("ERROR: failed to restore rounding rule");
}
```

The `volatile` qualifier (see [`volatile` Variables and
Fields](volatile.md)) is essential on x86 platforms to prevent an
optimizing compiler from producing the same value for both bounds.
