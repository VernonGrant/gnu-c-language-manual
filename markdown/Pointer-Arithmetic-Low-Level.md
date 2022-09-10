Next: [Pointer Increment and
Decrement](Pointer-Increment_002fDecrement.md), Previous: [Pointers
and Arrays](Pointers-and-Arrays.md), Up: [Pointers](Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 14.12 Pointer Arithmetic at Low Level 


The behavior of pointer arithmetic is theoretically defined only when
the pointer values all point within one object allocated in memory. But
the addition and subtraction operators can't tell whether the pointer
values are all within one object. They don't know where objects start
and end. So what do they really do?

Adding pointer `p`{.variable} to integer `i`{.variable} treats
`p`{.variable} as a memory address, which is in fact an integer---call
it `pint`{.variable}. It treats `i`{.variable} as a number of elements
of the type that `p`{.variable} points to. These elements' sizes add up
to `i * sizeof (*p)`. So the sum, as an integer, is
`pint + i * sizeof (*p)`. This value is reinterpreted as a pointer like
`p`{.variable}.

If the starting pointer value `p`{.variable} and the result do not point
at parts of the same object, the operation is not officially legitimate,
and C code is not "supposed" to do it. But you can do it anyway, and it
gives precisely the results described by the procedure above. In some
special situations it can do something useful, but non-wizards should
avoid it.

Here's a function to offset a pointer value *as if* it pointed to an
object of any given size, by explicitly performing that calculation:

``` C
#include <stdint.h>

void *
ptr_add (void *p, int i, int objsize)
{
  intptr_t p_address = (long) p;
  intptr_t totalsize = i * objsize;
  intptr_t new_address = p_address + totalsize;
  return (void *) new_address;
}
```

proper pointer type for `p`{.variable}. It uses the type `intptr_t`,
which is defined in the header file `stdint.h`. (In practice,
`long long` would always work, but it is cleaner to use `intptr_t`.)

------------------------------------------------------------------------

Next: [Pointer Increment and
Decrement](Pointer-Increment_002fDecrement.md), Previous: [Pointers
and Arrays](Pointers-and-Arrays.md), Up: [Pointers](Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
