Next: [Boolean Type](Boolean-Type.md), Previous: [Narrow
Integers](Narrow-Integers.md), Up: [Integer Data
Types](Integer-Types.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 11.1.4 Conversion among Integer Types 

C converts between integer types implicitly in many situations. It
converts the narrow integer types, `char` and `short`, to `int` whenever
they are used in arithmetic. Assigning a new value to an integer
variable (or other lvalue) converts the value to the variable's type.

You can also convert one integer type to another explicitly with a
*cast* operator. See [Explicit Type
Conversion](Explicit-Type-Conversion.md).

The process of conversion to a wider type is straightforward: the value
is unchanged. The only exception is when converting a negative value (in
a signed type, obviously) to a wider unsigned type. In that case, the
result is a positive value with the same bits (see [Integers in
Depth](Integers-in-Depth.md)).


Converting to a narrower type, also called *truncation*, involves
discarding some of the value's bits. This is not considered overflow
(see [Integer Overflow](Integer-Overflow.md)) because loss of
significant bits is a normal consequence of truncation. Likewise for
conversion between signed and unsigned types of the same width.

More information about conversion for assignment is in [Assignment Type
Conversions](Assignment-Type-Conversions.md). For conversion for
arithmetic, see [Argument Promotions](Argument-Promotions.md).
