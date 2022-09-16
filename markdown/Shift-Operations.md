Next: [Bitwise Operations](Bitwise-Operations.md), Previous: [Numeric
Comparisons](Numeric-Comparisons.md), Up:
[Arithmetic](Arithmetic.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 6.7 Shift Operations 


*Shifting* an integer means moving the bit values to the left or right
within the bits of the data type. Shifting is defined only for integers.
Here's the way to write it:

``` C
/* Left shift.  */
5 << 2 ⇒ 20

/* Right shift.  */
5 >> 2 ⇒ 1
```

The left operand is the value to be shifted, and the right operand says
how many bits to shift it (the *shift count*). The left operand is
promoted (see [Operand Promotions](Operand-Promotions.md)), so
shifting never operates on a narrow integer type; it's always either
`int` or wider. The result of the shift operation has the same type as
the promoted left operand.

-   [Shifting Makes New Bits](Bits-Shifted-In.md)
-   [Caveats for Shift Operations](Shift-Caveats.md)
-   [Shift Hacks](Shift-Hacks.md)
