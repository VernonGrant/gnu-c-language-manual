Next: [Postincrement and
Postdecrement](Postincrement_002fPostdecrement.md), Previous:
[Modifying Assignment](Modifying-Assignment.md), Up: [Assignment
Expressions](Assignment-Expressions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 7.4 Increment and Decrement Operators 


The operators '`++`' and '`--`' are the *increment*
and *decrement* operators. When used on a numeric value, they add or
subtract 1. We don't consider them assignments, but they are equivalent
to assignments.

Using '`++`' or '`--`' as a prefix, before an lvalue,
is called *preincrement* or *predecrement*. This adds or subtracts 1 and
the result becomes the expression's value. For instance,

``` C
#include <stdio.h>   /* Declares printf. */

int
main (void)
{
  int i = 5;
  printf ("%d\n", i);
  printf ("%d\n", ++i);
  printf ("%d\n", i);
  return 0;
}
```

prints lines containing 5, 6, and 6 again. The expression `++i`
increments `i` from 5 to 6, and has the value 6, so the output from
`printf` on that line says '`6`'.

Using '`--`' instead, for predecrement,

``` C
#include <stdio.h>   /* Declares printf. */

int
main (void)
{
  int i = 5;
  printf ("%d\n", i);
  printf ("%d\n", --i);
  printf ("%d\n", i);
  return 0;
}
```

prints three lines that contain (respectively) '`5`',
'`4`', and again '`4`'.
