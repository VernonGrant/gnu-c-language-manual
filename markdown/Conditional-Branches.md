Previous: [Rules for the Conditional Operator](Conditional-Rules.md),
Up: [Conditional Expression](Conditional-Expression.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 8.4.2 Conditional Operator Branches 


We call `iftrue` and `iffalse` the *branches* of
the conditional.

The two branches should normally have the same type, but a few
exceptions are allowed. If they are both numeric types, the conditional
converts both to their common type (see [Common
Type](Common-Type.md)).

With pointers (see [Pointers](Pointers.md)), the two values can be
pointers to nearly compatible types (see [Compatible
Types](Compatible-Types.md)). In this case, the result type is a
similar pointer whose target type combines all the type qualifiers (see
[Type Qualifiers](Type-Qualifiers.md)) of both branches.

If one branch has type `void *` and the other is a pointer to an object
(not to a function), the conditional converts the `void *` branch to the
type of the other.

If one branch is an integer constant with value zero and the other is a
pointer, the conditional converts zero to the pointer's type.

In GNU C, you can omit `iftrue` in a conditional expression.
In that case, if `condition` is nonzero, its value becomes
the value of the conditional expression, after conversion to the common
type. Thus,

``` C
x ? : y
```

has the value of `x` if that is nonzero; otherwise, the value of `y`.


Omitting `iftrue` is useful when `condition` has
side effects. In that case, writing that expression twice would carry
out the side effects twice, but writing it once does them just once. For
example, if we suppose that the function `next_element` advances a
pointer variable to point to the next element in a list and returns the
new pointer,

``` C
next_element () ? : default_pointer
```

is a way to advance the pointer and use its new value if it isn't null,
but use `default_pointer` if that is null. We cannot do it this way,

``` C
next_element () ? next_element () : default_pointer
```

because that would advance the pointer a second time.

------------------------------------------------------------------------

Previous: [Rules for the Conditional Operator](Conditional-Rules.md),
Up: [Conditional Expression](Conditional-Expression.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
