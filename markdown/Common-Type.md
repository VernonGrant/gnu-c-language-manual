Previous: [Operand Promotions](Operand-Promotions.md), Up: [Type
Conversions](Type-Conversions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 24.5 Common Type 


Arithmetic binary operators (except the shift operators) convert their
operands to the *common type* before operating on them. Conditional
expressions also convert the two possible results to their common type.
Here are the rules for determining the common type.

If one of the numbers has a floating-point type and the other is an
integer, the common type is that floating-point type. For instance,

``` C
5.6 * 2   ⇒ 11.2 /* a double value */
```

If both are floating point, the type with the larger range is the common
type.

If both are integers but of different widths, the common type is the
wider of the two.

If they are integer types of the same width, the common type is unsigned
if either operand is unsigned, and it's `long` if either operand is
`long`. It's `long long` if either operand is `long long`.

These rules apply to addition, subtraction, multiplication, division,
remainder, comparisons, and bitwise operations. They also apply to the
two branches of a conditional expression, and to the arithmetic done in
a modifying assignment operation.
