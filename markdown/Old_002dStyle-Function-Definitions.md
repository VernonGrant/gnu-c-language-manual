Previous: [Older GNU C Inlining](Old-GNU-Inlining.md), Up: [Obsolete
Function Features](Obsolete-Definitions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 22.8.2 Old-Style Function Definitions 


The syntax of C traditionally allows omitting the data type in a
function declaration if it specifies a storage class or a qualifier.
Then the type defaults to `int`. For example:

``` C
static foo (double x);
```

defaults the return type to `int`. This is bad practice; if you see it,
fix it.

An *old-style* (or "K&R") function definition is the way function
definitions were written in the 1980s. It looks like this:

``` C
rettype
function (parmnames)
  parm_declarations
{
  body
}
```

In `parmnames`{.variable}, only the parameter names are listed,
separated by commas. Then `parm_declarations`{.variable} declares their
data types; these declarations look just like variable declarations. If
a parameter is listed in `parmnames`{.variable} but has no declaration,
it is implicitly declared `int`.

There is no reason to write a definition this way nowadays, but they can
still be seen in older GNU programs.

An old-style variadic function definition looks like this:

``` C
#include <varargs.h>

int
add_multiple_values (va_alist)
    va_dcl
{
  int argcount;
  int counter, total = 0;

  /* Declare a variable of type va_list. */
  va_list argptr;

  /* Initialize that variable. */
  va_start (argptr);

  /* Get the first argument (fixed). */
  argcount = va_arg (int);

  for (counter = 0; counter < argcount; counter++)
    {
      /* Get the next additional argument. */
      total += va_arg (argptr, int);
    }

  /* End use of the argptr variable. */
  va_end (argptr);

  return total;
}
```

Note that the old-style variadic function definition has no fixed
parameter variables; all arguments must be obtained with `va_arg`.
