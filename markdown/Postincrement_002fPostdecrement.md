Next: [Pitfall: Assignment in
Subexpressions](Assignment-in-Subexpressions.md), Previous: [Increment
and Decrement Operators](Increment_002fDecrement.md), Up: [Assignment
Expressions](Assignment-Expressions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 7.5 Postincrement and Postdecrement 


Using '`++`' or '`--`' *after* an lvalue does
something peculiar: it gets the value directly out of the lvalue and
*then* increments or decrements it. Thus, the value of `i++` is the same
as the value of `i`, but `i++` also increments `i` "a little later."
This is called *postincrement* or *postdecrement*.

For example,

``` C
#include <stdio.h>   /* Declares printf. */

int
main (void)
{
  int i = 5;
  printf ("%d\n", i);
  printf ("%d\n", i++);
  printf ("%d\n", i);
  return 0;
}
```

prints lines containing 5, again 5, and 6. The expression `i++` has the
value 5, which is the value of `i` at the time, but it increments `i`
from 5 to 6 just a little later.

How much later is "just a little later"? That is flexible. The increment
has to happen by the next *sequence point*. In simple cases, that means
by the end of the statement. See [Sequence
Points](Sequence-Points.md).

If a unary operator precedes a postincrement or postincrement
expression, the increment nests inside:

``` C
-a++   is equivalent to   -(a++)
```

That's the only order that makes sense; `-a` is not an lvalue, so it
can't be incremented.
