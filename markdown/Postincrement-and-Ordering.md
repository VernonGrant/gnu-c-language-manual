Next: [Ordering of Operands](Ordering-of-Operands.md), Previous:
[Sequence Points](Sequence-Points.md), Up: [Order of
Execution](Order-of-Execution.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 10.4 Postincrement and Ordering 


Ordering requirements are loose with the postincrement and postdecrement
operations (see [Postincrement and
Postdecrement](Postincrement_002fPostdecrement.md)), which specify
side effects to happen "a little later." They must happen before the
next sequence point, but that still leaves room for various meanings. In
this expression,

``` C
z = x++ - foo ()
```

it's unpredictable whether `x` gets incremented before or after calling
the function `foo`. If `foo` refers to `x`, it might see the old value
or it might see the incremented value.

In this perverse expression,

``` C
x = x++
```

`x` will certainly be incremented but the incremented value may not
stick. If the incrementation of `x` happens after the assignment to `x`,
the incremented value will remain in place. But if the incrementation
happens first, the assignment will overwrite that with the
not-yet-incremented value, so the expression as a whole will leave `x`
unchanged.
