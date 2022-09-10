Next: [Further Reading](Further-Reading.md), Previous: [Complex
Arithmetic](Complex-Arithmetic.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 28.20 Round-Trip Base Conversion 


Most numeric programs involve converting between base-2 floating-point
numbers, as represented by the computer, and base-10 floating-point
numbers, as entered and handled by the programmer. What might not be
obvious is the number of base-2 bits vs. base-10 digits required for
each representation. Consider the following tables showing the number of
decimal digits representable in a given number of bits, and vice versa:

  ------------- ---- ---- ---- ----- -----
  binary in     24   53   64   113   237
  decimal out   9    17   21   36    73
  ------------- ---- ---- ---- ----- -----

  ------------ ---- ---- ----- -----
  decimal in   7    16   34    70
  binary out   25   55   114   234
  ------------ ---- ---- ----- -----

We can compute the table numbers with these two functions:

``` C
int
matula(int nbits)
{   /* Return output decimal digits needed for nbits-bits input. */
    return ((int)ceil((double)nbits / log2(10.0) + 1.0));
}

int
goldberg(int ndec)
{   /* Return output bits needed for ndec-digits input. */
    return ((int)ceil((double)ndec / log10(2.0) + 1.0));
}
```

One significant observation from those numbers is that we cannot achieve
correct round-trip conversion between the decimal and binary formats in
the same storage size! For example, we need 25 bits to represent a
7-digit value from the 32-bit decimal format, but the binary format only
has 24 available. Similar observations hold for each of the other
conversion pairs.

The general input/output base-conversion problem is astonishingly
complicated, and solutions were not generally known until the
publication of two papers in 1990 that are listed later near the end of
this chapter. For the 128-bit formats, the worst case needs more than
11,500 decimal digits of precision to guarantee correct rounding in a
binary-to-decimal conversion!

For further details see the references for Bennett Goldberg and David
Matula.

------------------------------------------------------------------------

Next: [Further Reading](Further-Reading.md), Previous: [Complex
Arithmetic](Complex-Arithmetic.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
