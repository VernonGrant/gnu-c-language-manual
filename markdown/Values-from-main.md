Next: [Accessing Command-line
Parameters](Command_002dline-Parameters.md), Up: [The `main`
Function](The-main-Function.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 22.6.1 Returning Values from `main` 


When `main` returns, the process terminates. Whatever value `main`
returns becomes the exit status which is reported to the parent process.
While nominally the return value is of type `int`, in fact the exit
status gets truncated to eight bits; if `main` returns the value 256,
the exit status is 0.

Normally, programs return only one of two values: 0 for success, and 1
for failure. For maximum portability, use the macro values
`EXIT_SUCCESS` and `EXIT_FAILURE` defined in `stdlib.h`. Here's an
example:


``` C
#include <stdlib.h>  /* Defines EXIT_SUCCESS */
                     /* and EXIT_FAILURE. */

int
main (void)
{
  …
  if (foo)
    return EXIT_SUCCESS;
  else
    return EXIT_FAILURE;
}
```

Some types of programs maintain special conventions for various return
values; for example, comparison programs including `cmp` and `diff`
return 1 to indicate a mismatch, and 2 to indicate that the comparison
couldn't be performed.
