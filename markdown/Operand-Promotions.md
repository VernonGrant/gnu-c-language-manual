Next: [Common Type](Common-Type.md), Previous: [Argument
Promotions](Argument-Promotions.md), Up: [Type
Conversions](Type-Conversions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 24.4 Operand Promotions 


The operands in arithmetic operations undergo type conversion
automatically. These *operand promotions* are the same as the argument
promotions except without converting `float` to `double`. In other
words, the operand promotions convert

-   `char` or `short` (whether signed or not) to `int`.
-   an array to a pointer to its zeroth element, and
-   a function name to a pointer to that function.
