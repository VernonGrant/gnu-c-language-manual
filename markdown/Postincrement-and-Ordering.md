Next: [Ordering of Operands](Ordering-of-Operands.md), Previous:
[Sequence Points](Sequence-Points.md), Up: [Order of
Execution](Order-of-Execution.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 10.4 Postincrement and Ordering 


The ordering requirements for the postincrement and postdecrement
operations (see [Postincrement and
Postdecrement](Postincrement_002fPostdecrement.md)) are loose: those
side effects must happen "a little later," before the next sequence
point. That still leaves room for various orders that give different
results. In this expression,

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

`x` will certainly be incremented but the incremented value may be
replaced with the old value. That's because the incrementation and the
assignment may occur in either oder. If the incrementation of `x` occurs
after the assignment to `x`, the incremented value will remain in place.
But if the incrementation happens first, the assignment will put the
not-yet-incremented value back into `x`, so the expression as a whole
will leave `x` unchanged.

The conclusion: **avoid such expressions**. Take care, when you use
postincrement and postdecrement, that the specific expression you use is
not ambiguous as to order of execution.
