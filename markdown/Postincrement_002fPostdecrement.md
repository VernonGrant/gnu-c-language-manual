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

How much later is "just a little later"? The compiler has some
flexibility in deciding that. The rule is that the increment has to
happen by the next *sequence point*; in simple cases, that means by the
end of the statement. See [Sequence Points](Sequence-Points.md).

Regardless of precisely where the compiled code increments the value of
`i`, the crucial thing is that the value of `i++` is the value that `i`
has *before* incrementing it.

If a unary operator precedes a postincrement or postincrement
expression, the increment nests inside:

``` C
-a++   is equivalent to   -(a++)
```

That's the only order that makes sense; `-a` is not an lvalue, so it
can't be incremented.

The most common use of postincrement is with arrays. Here's an example
of using postincrement to access one element of an array and advance the
index for the next access. Compare this with the example `avg_of_double`
(see [An Example with Arrays](Array-Example.md)), which is almost the
same but doesn't use postincrement.

``` C
double
avg_of_double_alt (int length, double input_data[])
{
  double sum = 0;
  int i;

  /* Fetch each element and add it into sum.  */
  for (i = 0; i < length;)
    /* Use the index i, then increment it.  */
    sum += input_data[i++];

  return sum / length;
}
```

------------------------------------------------------------------------

Next: [Pitfall: Assignment in
Subexpressions](Assignment-in-Subexpressions.md), Previous: [Increment
and Decrement Operators](Increment_002fDecrement.md), Up: [Assignment
Expressions](Assignment-Expressions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
