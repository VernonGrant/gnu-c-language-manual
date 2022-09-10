Next: [Modifying Assignment](Modifying-Assignment.md), Previous:
[Simple Assignment](Simple-Assignment.md), Up: [Assignment
Expressions](Assignment-Expressions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 7.2 Lvalues 


An expression that identifies a memory space that holds a value is
called an *lvalue*, because it is a location that can hold a value.

The standard kinds of lvalues are:

-   A variable.
-   A pointer-dereference expression (see [Dereferencing
    Pointers](Pointer-Dereference.md)) using unary '`*`'.
-   A structure field reference (see [Structures](Structures.md))
    using '`.`', if the structure value is an lvalue.
-   A structure field reference using '`->`'. This is always an
    lvalue since '`->`' implies pointer dereference.
-   A union alternative reference (see [Unions](Unions.md)), on the
    same conditions as for structure fields.
-   An array-element reference using '`[…]`', if the array is
    an lvalue.

If an expression's outermost operation is any other operator, that
expression is not an lvalue. Thus, the variable `x` is an lvalue, but
`x + 0` is not, even though these two expressions compute the same value
(assuming `x` is a number).

An array can be an lvalue (the rules above determine whether it is one),
but using the array in an expression converts it automatically to a
pointer to the first element. The result of this conversion is not an
lvalue. Thus, if the variable `a` is an array, you can't use `a` by
itself as the left operand of an assignment. But you can assign to an
element of `a`, such as `a[0]`. That is an lvalue since `a` is an
lvalue.
