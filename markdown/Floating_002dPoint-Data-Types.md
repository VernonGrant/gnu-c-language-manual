Next: [Complex Data Types](Complex-Data-Types.md), Previous: [Integer
Data Types](Integer-Types.md), Up: [Primitive Data
Types](Primitive-Types.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 11.2 Floating-Point Data Types 


*Floating point* is the binary analogue of scientific notation:
internally it represents a number as a fraction and a binary exponent;
the value is that fraction multiplied by the specified power of 2.

For instance, to represent 6, the fraction would be 0.75 and the
exponent would be 3; together they stand for the value *0.75 \* 2^3^*,
meaning 0.75 \* 8. The value 1.5 would use 0.75 as the fraction and 1 as
the exponent. The value 0.75 would use 0.75 as the fraction and 0 as the
exponent. The value 0.375 would use 0.75 as the fraction and -1 as the
exponent.

These binary exponents are used by machine instructions. You can write a
floating-point constant this way if you wish, using hexadecimal; but
normally we write floating-point numbers in decimal. See [Floating-Point
Constants](Floating-Constants.md).

C has three floating-point data types:

`double`

-   "Double-precision" floating point, which uses 64 bits. This is the
    normal floating-point type, and modern computers normally do their
    floating-point computations in this type, or some wider type. Except
    when there is a special reason to do otherwise, this is the type to
    use for floating-point values.

`float`

-   "Single-precision" floating point, which uses 32 bits. It is useful
    for floating-point values stored in structures and arrays, to save
    space when the full precision of `double` is not needed. In
    addition, single-precision arithmetic is faster on some computers,
    and occasionally that is useful. But not often---most programs don't
    use the type `float`.

    C would be cleaner if `float` were the name of the type we use for
    most floating-point values; however, for historical reasons, that's
    not so.

`long double`

-   "Extended-precision" floating point is either 80-bit or 128-bit
    precision, depending on the machine in use. On some machines, which
    have no floating-point format wider than `double`, this is
    equivalent to `double`.

Floating-point arithmetic raises many subtle issues. See [Floating Point
in Depth](Floating-Point-in-Depth.md), for more information.

------------------------------------------------------------------------

Next: [Complex Data Types](Complex-Data-Types.md), Previous: [Integer
Data Types](Integer-Types.md), Up: [Primitive Data
Types](Primitive-Types.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
