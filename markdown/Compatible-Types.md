Next: [Type Conversions](Type-Conversions.md), Previous:
[Functions](Functions.md), Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


## 23 Compatible Types 


Declaring a function or variable twice is valid in C only if the two
declarations specify *compatible* types. In addition, some operations on
pointers require operands to have compatible target types.

In C, two different primitive types are never compatible. Likewise for
the defined types `struct`, `union` and `enum`: two separately defined
types are incompatible unless they are defined exactly the same way.

However, there are a few cases where different types can be compatible:

-   Every enumeration type is compatible with some integer type. In GNU
    C, the choice of integer type depends on the largest enumeration
    value.
-   Array types are compatible if the element types are compatible and
    the sizes (when specified) match.
-   Pointer types are compatible if the pointer target types are
    compatible.
-   Function types that specify argument types are compatible if the
    return types are compatible and the argument types are compatible,
    argument by argument. In addition, they must all agree in whether
    they use `...` to allow additional arguments.
-   Function types that don't specify argument types are compatible if
    the return types are.
-   Function types that specify the argument types are compatible with
    function types that omit them, if the return types are compatible
    and the specified argument types are unaltered by the argument
    promotions (see [Argument Promotions](Argument-Promotions.md)).

In order for types to be compatible, they must agree in their type
qualifiers. Thus, `const int` and `int` are incompatible. It follows
that `const int *` and `int *` are incompatible too (they are pointers
to types that are not compatible).

If two types are compatible ignoring the qualifiers, we call them
*nearly compatible*. (If they are array types, we ignore qualifiers on
the element types.[^7^](#FOOT7)) Comparison of pointers is valid
if the pointers' target types are nearly compatible. Likewise, the two
branches of a conditional expression may be pointers to nearly
compatible target types.

If two types are compatible ignoring the qualifiers, and the first type
has all the qualifiers of the second type, we say the first is *upward
compatible* with the second. Assignment of pointers requires the
assigned pointer's target type to be upward compatible with the right
operand (the new value)'s target type.


------------------------------------------------------------------------

#### Footnotes 

##### [(7)](#DOCF7)

This is a GNU C extension.

------------------------------------------------------------------------

Next: [Type Conversions](Type-Conversions.md), Previous:
[Functions](Functions.md), Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
