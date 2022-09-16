Next: [Imaginary Constants](Imaginary-Constants.md), Previous:
[Integer Constant Data Types](Integer-Const-Type.md), Up:
[Constants](Constants.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 12.3 Floating-Point Constants 


A floating-point constant must have either a decimal point, an
exponent-of-ten, or both; they distinguish it from an integer constant.

To indicate an exponent, write '`e`' or '`E`'. The
exponent value follows. It is always written as a decimal number; it can
optionally start with a sign. The exponent `n` means to
multiply the constant's value by ten to the `n`th power.

Thus, '`1500.0`', '`15e2`', '`15e+2`',
'`15.0e2`', '`1.5e+3`', '`.15e4`', and
'`15000e-1`' are six ways of writing a floating-point number
whose value is 1500. They are all equivalent.

Here are more examples with decimal points:

``` C
1.0
1000.
3.14159
.05
.0005
```

For each of them, here are some equivalent constants written with
exponents:

``` C
1e0, 1.0000e0
100e1, 100e+1, 100E+1, 1e3, 10000e-1
3.14159e0
5e-2, .0005e+2, 5E-2, .0005E2
.05e-2
```

A floating-point constant normally has type `double`. You can force it
to type `float` by adding '`f`' or '`F`' at the end.
For example,

``` C
3.14159f
3.14159e0f
1000.f
100E1F
.0005f
.05e-2f
```

Likewise, '`l`' or '`L`' at the end forces the
constant to type `long double`.

You can use exponents in hexadecimal floating constants, but since
'`e`' would be interpreted as a hexadecimal digit, the
character '`p`' or '`P`' (for "power") indicates an
exponent.

The exponent in a hexadecimal floating constant is an optionally signed
decimal integer that specifies a power of 2 (*not* 10 or 16) to multiply
into the number.

Here are some examples:

``` C
0xAp2        // 40 in decimal
0xAp-1       // 5 in decimal
0x2.0Bp4     // 16.75 decimal
0xE.2p3      // 121 decimal
0x123.ABCp0  // 291.6708984375 in decimal
0x123.ABCp4  // 4666.734375 in decimal
0x100p-8     // 1
0x10p-4      // 1
0x1p+4       // 16
0x1p+8       // 256
```

See [Floating-Point Data Types](Floating_002dPoint-Data-Types.md).

------------------------------------------------------------------------

Next: [Imaginary Constants](Imaginary-Constants.md), Previous:
[Integer Constant Data Types](Integer-Const-Type.md), Up:
[Constants](Constants.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
