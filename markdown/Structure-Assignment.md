Next: [Unions](Unions.md), Previous: [Overlaying Different
Structures](Overlaying-Structures.md), Up:
[Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.12 Structure Assignment 


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
