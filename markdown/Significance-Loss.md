Next: [Fused Multiply-Add](Fused-Multiply_002dAdd.md), Previous:
[Rounding Issues](Rounding-Issues.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 28.9 Significance Loss 


A much more serious source of error in floating-point computation is
*significance loss* from subtraction of nearly equal values. This means
that the number of bits in the significand of the result is fewer than
the size of the value would permit. If the values being subtracted are
close enough, but still not equal, a *single subtraction* can wipe out
all correct digits, possibly contaminating all future computations.

Floating-point calculations can sometimes be carefully designed so that
significance loss is not possible, such as summing a series where all
terms have the same sign. For example, the Taylor series expansions of
the trigonometric and hyperbolic sines have terms of identical
magnitude, of the general form `x**(2*n + 1) / (2*n + 1)!`. However,
those in the trigonometric sine series alternate in sign, while those in
the hyperbolic sine series are all positive. Here is the output of two
small programs that sum `k`{.variable} terms of the series for
`sin (x)`, and compare the computed sums with known-to-be-accurate
library functions:

``` C
x = 10      k = 51
s (x)   = -0.544_021_110_889_270
sin (x) = -0.544_021_110_889_370

x = 20      k = 81
s (x)   = 0.912_945_250_749_573
sin (x) = 0.912_945_250_727_628

x = 30      k = 109
s (x)   = -0.987_813_746_058_855
sin (x) = -0.988_031_624_092_862

x = 40      k = 137
s (x)   = 0.617_400_430_980_474
sin (x) = 0.745_113_160_479_349

x = 50      k = 159
s (x)   = 57_105.187_673_745_720_532
sin (x) = -0.262_374_853_703_929

// sinh(x) series summation with positive signs
// with k terms needed to converge to machine precision

x = 10      k = 47
t (x)    = 1.101_323_287_470_340e+04
sinh (x) = 1.101_323_287_470_339e+04

x = 20      k = 69
t (x)    = 2.425_825_977_048_951e+08
sinh (x) = 2.425_825_977_048_951e+08

x = 30      k = 87
t (x)    = 5.343_237_290_762_229e+12
sinh (x) = 5.343_237_290_762_231e+12

x = 40      k = 105
t (x)    = 1.176_926_334_185_100e+17
sinh (x) = 1.176_926_334_185_100e+17

x = 50      k = 121
t (x)    = 2.592_352_764_293_534e+21
sinh (x) = 2.592_352_764_293_536e+21
```

We have added underscores to the numbers to enhance readability.

The `sinh (x)` series with positive terms can be summed to high
accuracy. By contrast, the series for `sin (x)` suffers increasing
significance loss, so that when `x`{.variable} = 30 only two correct
digits remain. Soon after, all digits are wrong, and the answers are
complete nonsense.

An important skill in numerical programming is to recognize when
significance loss is likely to contaminate a computation, and revise the
algorithm to reduce this problem. Sometimes, the only practical way to
do so is to compute in higher intermediate precision, which is why the
extended types like `long double` are important.

------------------------------------------------------------------------

Next: [Fused Multiply-Add](Fused-Multiply_002dAdd.md), Previous:
[Rounding Issues](Rounding-Issues.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
