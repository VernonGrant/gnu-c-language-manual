Next: [Complete Program Explanation](Complete-Explanation.md), Up: [A
Complete Program](Complete-Program.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 2.1 Complete Program Example 

Here is the complete program that uses the simple, recursive version of
the `fib` function (see [Example: Recursive
Fibonacci](Recursive-Fibonacci.md)):

``` C
#include <stdio.h>

int
fib (int n)
{
  if (n <= 2)  /* This avoids infinite recursion.  */
    return 1;
  else
    return fib (n - 1) + fib (n - 2);
}

int
main (void)
{
  printf ("Fibonacci series item %d is %d\n",
          20, fib (20));
  return 0;
}
```

This program prints a message that shows the value of `fib (20)`.

Now for an explanation of what that code means.
