Next: [Type qualifiers on array parameters](Array-Parm-Qualifiers.md),
Previous: [Array parameters are pointers](Array-Parm-Pointer.md), Up:
[Arrays as Parameters](Arrays-as-Parameters.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 22.1.4.2 Passing array arguments 

The function call passes this pointer by value, like all argument values
in C. However, the result is paradoxical in that the array itself is
passed by reference: its contents are treated as shared memory---shared
between the caller and the called function, that is. When `clobber4`
assigns to element 4 of `array`, the effect is to alter element 4 of the
array specified in the call.

``` C
#include <stddef.h>  /* Defines NULL. */
#include <stdlib.h>  /* Declares malloc, */
                     /* Defines EXIT_SUCCESS. */

int
main (void)
{
  int data[] = {1, 2, 3, 4, 5, 6};
  int i;

  /* Show the initial value of element 4. */
  for (i = 0; i < 6; i++)
    printf ("data[%d] = %d\n", i, data[i]);

  printf ("\n");

  clobber4 (data);

  /* Show that element 4 has been changed. */
  for (i = 0; i < 6; i++)
    printf ("data[%d] = %d\n", i, data[i]);

  printf ("\n");

  return EXIT_SUCCESS;
}
```

shows that `data[4]` has become zero after the call to `clobber4`.

The array `data` has 6 elements, but passing it to a function whose
argument type is written as `int [20]` is not an error, because that
really stands for `int *`. The pointer that is the real argument carries
no indication of the length of the array it points into. It is not
required to point to the beginning of the array, either. For instance,

``` C
clobber4 (data+1);
```

passes an "array" that starts at element 1 of `data`, and the effect is
to zero `data[5]` instead of `data[4]`.

If all calls to the function will provide an array of a particular size,
you can specify the size of the array to be `static`:

``` C
void
clobber4 (int array[static 20])
…
```

This is a promise to the compiler that the function will always be
called with an array of 20 elements, so that the compiler can optimize
code accordingly. If the code breaks this promise and calls the function
with, for example, a shorter array, unpredictable things may happen.

------------------------------------------------------------------------

Next: [Type qualifiers on array parameters](Array-Parm-Qualifiers.md),
Previous: [Array parameters are pointers](Array-Parm-Pointer.md), Up:
[Arrays as Parameters](Arrays-as-Parameters.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
