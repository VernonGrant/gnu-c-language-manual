Previous: [Constructing Array Values](Constructing-Array-Values.md),
Up: [Arrays](Arrays.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 16.9 Arrays of Variable Length 


In GNU C, you can declare variable-length arrays like any other arrays,
but with a length that is not a constant expression. The storage is
allocated at the point of declaration and deallocated when the block
scope containing the declaration exits. For example:

``` C
#include <stdio.h>  /* Defines FILE. */
#include <string.h> /* Declares str. */

FILE *
concat_fopen (char *s1, char *s2, char *mode)
{
  char str[strlen (s1) + strlen (s2) + 1];
  strcpy (str, s1);
  strcat (str, s2);
  return fopen (str, mode);
}
```

(This uses some standard library functions; see [String and Array
Utilities](https://www.gnu.org/software/libc/manual/html_node/String-and-Array-Utilities.md#String-and-Array-Utilities)
in The GNU C Library Reference Manual.)

The length of an array is computed once when the storage is allocated
and is remembered for the scope of the array in case it is used in
`sizeof`.

**Warning:** don't allocate a variable-length array if the size might be
very large (more than 100,000), or in a recursive function, because that
is likely to cause stack overflow. Allocate the array dynamically
instead (see [Dynamic Memory
Allocation](Dynamic-Memory-Allocation.md)).

Jumping or breaking out of the scope of the array name deallocates the
storage. Jumping into the scope is not allowed; that gives an error
message.

You can also use variable-length arrays as arguments to functions:

``` C
struct entry
tester (int len, char data[len][len])
{
  …
}
```

As usual, a function argument declared with an array type is really a
pointer to an array that already exists. Calling the function does not
allocate the array, so there's no particular danger of stack overflow in
using this construct.

To pass the array first and the length afterward, use a forward
declaration in the function's parameter list (another GNU extension).
For example,

``` C
struct entry
tester (int len; char data[len][len], int len)
{
  …
}
```

The `int len` before the semicolon is a *parameter forward declaration*,
and it serves the purpose of making the name `len` known when the
declaration of `data` is parsed.

You can write any number of such parameter forward declarations in the
parameter list. They can be separated by commas or semicolons, but the
last one must end with a semicolon, which is followed by the "real"
parameter declarations. Each forward declaration must match a "real"
declaration in parameter name and data type. ISO C11 does not support
parameter forward declarations.

------------------------------------------------------------------------

Previous: [Constructing Array Values](Constructing-Array-Values.md),
Up: [Arrays](Arrays.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
