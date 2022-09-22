Next: [Unions](Unions.md), Previous: [Overlaying Different
Structures](Overlaying-Structures.md), Up:
[Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.13 Structure Assignment 


Assignment operating on a structure type copies the structure. The left
and right operands must have the same type. Here is an example:

``` C
#include <stddef.h>  /* Defines NULL. */
#include <stdlib.h>  /* Declares malloc.  */
…

struct point { double x, y; };

struct point *
copy_point (struct point point)
{
  struct point *p
    = (struct point *) malloc (sizeof (struct point));
  if (p == NULL)
    fatal ("Out of memory");
  *p = point;
  return p;
}
```

Notionally, assignment on a structure type works by copying each of the
fields. Thus, if any of the fields has the `const` qualifier, that
structure type does not allow assignment:

``` C
struct point { const double x, y; };

struct point a, b;

a = b;            /* Error! */
```

See [Assignment Expressions](Assignment-Expressions.md).

When a structure type has a field which is an array, as here,

``` C
struct record
  {
    char *name;
    int data[4];
  };

struct record r1, r2;
```

structure assigment such as `r1 = r2` copies array fields' contents just
as it copies all the other fields.

This is the only way in C that you can operate on the whole contents of
a array with one operation: when the array is contained in a `struct`.
You can't copy the contents of the `data` field as an array, because

``` C
r1.data = r2.data;
```

would convert the array objects (as always) to pointers to the zeroth
elements of the arrays (of type `struct record *`), and the assignment
would be invalid because the left operand is not an lvalue.

------------------------------------------------------------------------

Next: [Unions](Unions.md), Previous: [Overlaying Different
Structures](Overlaying-Structures.md), Up:
[Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
