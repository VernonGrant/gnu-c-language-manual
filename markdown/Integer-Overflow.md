Next: [Mixed-Mode Arithmetic](Mixed-Mode.md), Previous: [Integer
Arithmetic](Integer-Arithmetic.md), Up: [Arithmetic](Arithmetic.md)
 
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 6.3 Integer Overflow 


When the mathematical value of an arithmetic operation doesn't fit in
the range of the data type in use, that's called *overflow*. When it
happens in integer arithmetic, it is *integer overflow*.

Integer overflow happens only in arithmetic operations. Type conversion
operations, by definition, do not cause overflow, not even when the
result can't fit in its new type. See [Conversion among Integer
Types](Integer-Conversion.md).

Signed numbers use two's-complement representation, in which the most
negative number lacks a positive counterpart (see [Integers in
Depth](Integers-in-Depth.md)). Thus, the unary '`-`' operator
on a signed integer can overflow.

-   [Overflow with Unsigned Integers](Unsigned-Overflow.md)
-   [Overflow with Signed Integers](Signed-Overflow.md)
