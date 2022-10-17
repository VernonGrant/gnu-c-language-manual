Next: [Significance Loss](Significance-Loss.md), Previous:
[Rounding](Rounding.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 28.8 Rounding Issues 


The default IEEE 754 rounding mode minimizes errors, and most normal
computations should not suffer any serious accumulation of errors from
rounding.

Of course, you can contrive examples where that is not so. Here is one:
iterate a square root, then attempt to recover the original value by
repeated squaring.

``` C
#include <stdio.h>
#include <math.h>

int main (void)
{
  double x = 100.0;
  double y;
  int n, k;
  for (n = 10; n <= 100; n += 10)
    {
      y = x;
      for (k = 0; k < n; ++k) y = sqrt (y);
      for (k = 0; k < n; ++k) y *= y;
      printf ("n = %3d; x = %.0f\ty = %.6f\n", n, x, y);
    }
  return 0;
}
```

Here is the output:

``` C
n =  10; x = 100        y = 100.000000
n =  20; x = 100        y = 100.000000
n =  30; x = 100        y = 99.999977
n =  40; x = 100        y = 99.981025
n =  50; x = 100        y = 90.017127
n =  60; x = 100        y = 1.000000
n =  70; x = 100        y = 1.000000
n =  80; x = 100        y = 1.000000
n =  90; x = 100        y = 1.000000
n = 100; x = 100        y = 1.000000
```

After 50 iterations, `y` has barely one correct digit, and soon after,
there are no correct digits.
