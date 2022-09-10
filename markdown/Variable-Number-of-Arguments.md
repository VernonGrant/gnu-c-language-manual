Next: [Nested Functions](Nested-Functions.md), Previous:
[Variable-Length Array
Parameters](Variable_002dLength-Array-Parameters.md), Up: [Advanced
Function Features](Advanced-Definitions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 22.7.2 Variable-Length Parameter Lists 


A function that takes a variable number of arguments is called a
*variadic function*. In C, a variadic function must specify at least one
fixed argument with an explicitly declared data type. Additional
arguments can follow, and can vary in both quantity and data type.

In the function header, declare the fixed parameters in the normal way,
then write a comma and an ellipsis: '`, ...`'. Here is an
example of a variadic function header:

``` C
int add_multiple_values (int number, ...)
```


The function body can refer to fixed arguments by their parameter names,
but the additional arguments have no names. Accessing them in the
function body uses certain standard macros. They are defined in the
library header file `stdarg.h`, so the code must `#include`
that file.

In the body, write

``` C
va_list ap;
va_start (ap, last_fixed_parameter);
```

This declares the variable `ap` (you can use any name for it) and then
sets it up to point before the first additional argument.

Then, to fetch the next consecutive additional argument, write this:

``` C
va_arg (ap, type)
```

After fetching all the additional arguments (or as many as need to be
used), write this:

``` C
va_end (ap);
```

Here's an example of a variadic function definition that adds any number
of `int` arguments. The first (fixed) argument says how many more
arguments follow.

``` C
#include <stdarg.h> /* Defines va… macros. */
…

int
add_multiple_values (int argcount, ...)
{
  int counter, total = 0;

  /* Declare a variable of type va_list. */
  va_list argptr;

  /* Initialize that variable.. */
  va_start (argptr, argcount);

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

With GNU C, `va_end` is superfluous, but some other compilers might make
`va_start` allocate memory so that calling `va_end` is necessary to
avoid a memory leak. Before doing `va_start` again with the same
variable, do `va_end` first.


Because of this possible memory allocation, it is risky (in principle)
to copy one `va_list` variable to another with assignment. Instead, use
`va_copy`, which copies the substance but allocates separate memory in
the variable you copy to. The call looks like `va_copy (to, from)`,
where both `to` and `from` should be variables of
type `va_list`. In principle, do `va_end` on each of these variables
before its scope ends.

Since the additional arguments' types are not specified in the
function's definition, the default argument promotions (see [Argument
Promotions](Argument-Promotions.md)) apply to them in function calls.
The function definition must take account of this; thus, if an argument
was passed as `short`, the function should get it as `int`. If an
argument was passed as `float`, the function should get it as `double`.

C has no mechanism to tell the variadic function how many arguments were
passed to it, so its calling convention must give it a way to determine
this. That's why `add_multiple_values` takes a fixed argument that says
how many more arguments follow. Thus, you can call the function like
this:

``` C
sum = add_multiple_values (3, 12, 34, 190);
/* Value is 12+34+190. */
```

In GNU C, there is no actual need to use the `va_end` function. In fact,
it does nothing. It's used for compatibility with other compilers, when
that matters.

It is a mistake to access variables declared as `va_list` except in the
specific ways described here. Just what that type consists of is an
implementation detail, which could vary from one platform to another.

------------------------------------------------------------------------

Next: [Nested Functions](Nested-Functions.md), Previous:
[Variable-Length Array
Parameters](Variable_002dLength-Array-Parameters.md), Up: [Advanced
Function Features](Advanced-Definitions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
