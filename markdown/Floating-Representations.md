Next: [Floating-Point Type Specifications](Floating-Type-Specs.md),
Up: [Floating Point in Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 28.1 Floating-Point Representations 


Storing numbers as *floating point* allows representation of numbers
with fractional values, in a range larger than that of hardware
integers. A floating-point number consists of a sign bit, a
*significand* (also called the *mantissa*), and a power of a fixed base.
GNU C uses the floating-point representations specified by the IEEE
754-2008 Standard for Floating-Point Arithmetic.

The IEEE 754-2008 specification defines basic binary floating-point
formats of five different sizes: 16-bit, 32-bit, 64-bit, 128-bit, and
256-bit. The formats of 32, 64, and 128 bits are used for the standard C
types `float`, `double`, and `long double`. GNU C supports the 16-bit
floating point type `_Float16` on some platforms, but does not support
the 256-bit floating point type.

Each of the formats encodes the floating-point number as a sign bit.
After this comes an exponent that specifies a power of 2 (with a fixed
offset). Then comes the significand.

The first bit of the significand, before the binary point, is always 1,
so there is no need to store it in memory. It is called the *hidden bit*
because it doesn't appear in the floating-point number as used in the
computer itself.

All of those floating-point formats are sign-magnitude representations,
so +0 and -0 are different values.

Besides the IEEE 754 format 128-bit float, GNU C also offers a format
consisting of a pair of 64-bit floating point numbers. This lacks the
full exponent range of the IEEE 128-bit format, but is useful when the
underlying hardware platform does not support that.

------------------------------------------------------------------------

Next: [Floating-Point Type Specifications](Floating-Type-Specs.md),
Up: [Floating Point in Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
