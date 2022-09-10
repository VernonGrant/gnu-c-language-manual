Next: [Caveats for Shift Operations](Shift-Caveats.md), Up: [Shift
Operations](Shift-Operations.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 6.7.1 Shifting Makes New Bits 

A shift operation shifts towards one end of the number and has to
generate new bits at the other end.

Shifting left one bit must generate a new least significant bit. It
always brings in zero there. It is equivalent to multiplying by the
appropriate power of 2. For example,

``` C
5 << 3     is equivalent to   5 * 2*2*2
-10 << 4   is equivalent to   -10 * 2*2*2*2
```

The meaning of shifting right depends on whether the data type is signed
or unsigned (see [Signed and Unsigned
Types](Signed-and-Unsigned-Types.md)). For a signed data type, it
performs "arithmetic shift," which keeps the number's sign unchanged by
duplicating the sign bit. For an unsigned data type, it performs
"logical shift," which always shifts in zeros at the most significant
bit.

In both cases, shifting right one bit is division by two, rounding
towards negative infinity. For example,

``` C
(unsigned) 19 >> 2 ⇒ 4
(unsigned) 20 >> 2 ⇒ 5
(unsigned) 21 >> 2 ⇒ 5
```

For negative left operand `a`, `a >> 1` is not equivalent to `a / 2`.
They both divide by 2, but '`/`' rounds toward zero.

The shift count must be zero or greater. Shifting by a negative number
of bits gives machine-dependent results.
