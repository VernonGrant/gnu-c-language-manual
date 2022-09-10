Next: [Pointer Types](Pointer-Types.md), Up: [Pointers](Pointers.md)
 
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 14.1 Address of Data 


The most basic way to make a pointer is with the "address-of" operator,
'`&`'. Let's suppose we have these variables available:

``` C
int i;
double a[5];
```

Now, `&i` gives the address of the variable `i`---a pointer value that
points to `i`'s location---and `&a[3]` gives the address of the element
3 of `a`. (It is actually the fourth element in the array, since the
first element has index 0.)

The address-of operator is unusual because it operates on a place to
store a value (an lvalue, see [Lvalues](Lvalues.md)), not on the value
currently stored there. (The left argument of a simple assignment is
unusual in the same way.) You can use it on any lvalue except a bit
field (see [Bit Fields](Bit-Fields.md)) or a constructor (see
[Structure Constructors](Structure-Constructors.md)).
