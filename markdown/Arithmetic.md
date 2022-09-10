Next: [Assignment Expressions](Assignment-Expressions.md), Previous:
[Lexical Syntax](Lexical-Syntax.md), Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


## 6 Arithmetic 


Arithmetic operators in C attempt to be as similar as possible to the
abstract arithmetic operations, but it is impossible to do this
perfectly. Numbers in a computer have a finite range of possible values,
and non-integer values have a limit on their possible accuracy.
Nonetheless, in most cases you will encounter no surprises in using
'`+`' for addition, '`-`' for subtraction, and
'`*`' for multiplication.

Each C operator has a *precedence*, which is its rank in the grammatical
order of the various operators. The operators with the highest
precedence grab adjoining operands first; these expressions then become
operands for operators of lower precedence. We give some information
about precedence of operators in this chapter where we describe the
operators; for the full explanation, see [Binary Operator
Grammar](Binary-Operator-Grammar.md).

The arithmetic operators always *promote* their operands before
operating on them. This means converting narrow integer data types to a
wider data type (see [Operand Promotions](Operand-Promotions.md)). If
you are just learning C, don't worry about this yet.

Given two operands that have different types, most arithmetic operations
convert them both to their *common type*. For instance, if one is `int`
and the other is `double`, the common type is `double`. (That's because
`double` can represent all the values that an `int` can hold, but not
vice versa.) For the full details, see [Common Type](Common-Type.md).

-   [Basic Arithmetic](Basic-Arithmetic.md)
-   [Integer Arithmetic](Integer-Arithmetic.md)
-   [Integer Overflow](Integer-Overflow.md)
-   [Mixed-Mode Arithmetic](Mixed-Mode.md)
-   [Division and Remainder](Division-and-Remainder.md)
-   [Numeric Comparisons](Numeric-Comparisons.md)
-   [Shift Operations](Shift-Operations.md)
-   [Bitwise Operations](Bitwise-Operations.md)

------------------------------------------------------------------------

Next: [Assignment Expressions](Assignment-Expressions.md), Previous:
[Lexical Syntax](Lexical-Syntax.md), Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
