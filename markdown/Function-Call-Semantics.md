Next: [Function Pointers](Function-Pointers.md), Previous: [Function
Calls](Function-Calls.md), Up: [Functions](Functions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 22.4 Function Call Semantics 


The meaning of a function call is to compute the specified argument
expressions, convert their values according to the function's
declaration, then run the function giving it copies of the converted
values. (This method of argument passing is known as *call-by-value*.)
When the function finishes, the value it returns becomes the value of
the function-call expression.

Call-by-value implies that an assignment to the function argument
variable has no direct effect on the caller. For instance,

``` C
#include <stdlib.h>  /* Defines EXIT_SUCCESS. */
#include <stdio.h>   /* Declares printf. */

void
subroutine (int x)
{
  x = 5;
}

void
main (void)
{
  int y = 20;
  subroutine (y);
  printf ("y is %d\n", y);
  return EXIT_SUCCESS;
}
```

prints '`y is 20`'. Calling `subroutine` initializes `x` from
the value of `y`, but this does not establish any other relationship
between the two variables. Thus, the assignment to `x`, inside
`subroutine`, changes only *that* `x`.

If an argument's type is specified by the function's declaration, the
function call converts the argument expression to that type if possible.
If the conversion is impossible, that is an error.

If the function's declaration doesn't specify the type of that argument,
then the *default argument promotions* apply. See [Argument
Promotions](Argument-Promotions.md).
