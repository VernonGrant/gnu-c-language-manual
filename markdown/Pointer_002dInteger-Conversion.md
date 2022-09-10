Next: [Printing Pointers](Printing-Pointers.md), Previous: [Drawbacks
of Pointer Arithmetic](Pointer-Arithmetic-Drawbacks.md), Up:
[Pointers](Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 14.15 Pointer-Integer Conversion 


On modern computers, an address is simply a number. It occupies the same
space as some size of integer. In C, you can convert a pointer to the
appropriate integer types and vice versa, without losing information.
The appropriate integer types are `uintptr_t` (an unsigned type) and
`intptr_t` (a signed type). Both are defined in `stdint.h`.

For instance,

``` C
#include <stdint.h>
#include <stdio.h>

void
print_pointer (void *ptr)
{
  uintptr_t converted = (uintptr_t) ptr;

  printf ("Pointer value is 0x%x\n",
          (unsigned int) converted);
}
```

The specification '`%x`' in the template (the first argument)
for `printf` means to represent this argument using hexadecimal
notation. It's cleaner to use `uintptr_t`, since hexadecimal printing
treats the number as unsigned, but it won't actually matter: all
`printf` gets to see is the series of bits in the number.

**Warning:** Converting pointers to integers is risky---don't do it
unless it is really necessary.
