Next: [Compiling the Example Program](Compile-Example.md), Previous:
[Complete Program Explanation](Complete-Explanation.md), Up: [A
Complete Program](Complete-Program.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 2.3 Complete Program, Line by Line 

Here's the same example, explained line by line. **Beginners, do you
find this helpful or not? Would you prefer a different layout for the
example? Please tell rms\@gnu.org.**

``` C
#include <stdio.h>      /* Include declaration of usual */
                        /*   I/O functions such as printf.  */
                        /* Most programs need these.  */

int                     /* This function returns an int.  */
fib (int n)             /* Its name is fib;  */
                        /*   its argument is called n.  */
{                       /* Start of function body.  */
  /* This stops the recursion from being infinite.  */
  if (n <= 2)           /* If n is 1 or 2,  */
    return 1;           /*   make fib return 1.  */
  else                  /* otherwise, add the two previous  */
                        /* fibonacci numbers.  */
    return fib (n - 1) + fib (n - 2);
}

int                     /* This function returns an int.  */
main (void)             /* Start here; ignore arguments.  */
{                       /* Print message with numbers in it.  */
  printf ("Fibonacci series item %d is %d\n",
          20, fib (20));
  return 0;             /* Terminate program, report success.  */
}
```
