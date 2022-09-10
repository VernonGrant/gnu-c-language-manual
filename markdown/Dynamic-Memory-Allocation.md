Next: [Field Offset](Field-Offset.md), Previous: [Referencing
Structure Fields](Referencing-Fields.md), Up:
[Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.2 Dynamic Memory Allocation 


To allocate an object dynamically, call the library function `malloc`
(see [The GNU C
Library](https://www.gnu.org/software/libc/manual/html_node/Basic-Allocation.md#Basic-Allocation)
in The GNU C Library Reference Manual). Here is how to allocate an
object of type `struct intlistlink`. To make this code work, include the
file `stdlib.h`, like this:

``` C
#include <stddef.h>  /* Defines NULL. */
#include <stdlib.h>  /* Declares malloc.  */

…

struct intlistlink *
alloc_intlistlink ()
{
  struct intlistlink *p;

  p = malloc (sizeof (struct intlistlink));

  if (p == NULL)
    fatal ("Ran out of storage");

  /* Initialize the contents. */
  p->datum = 0;
  p->next = NULL;

  return p;
}
```

`malloc` returns `void *`, so the assignment to `p` will automatically
convert it to type `struct intlistlink *`. The return value of `malloc`
is always sufficiently aligned (see [Type
Alignment](Type-Alignment.md)) that it is valid for any data type.

The test for `p == NULL` is necessary because `malloc` returns a null
pointer if it cannot get any storage. We assume that the program defines
the function `fatal` to report a fatal error to the user.

Here's how to add one more integer to the front of such a list:

``` C
struct intlistlink *my_list = NULL;

void
add_to_mylist (int my_int)
{
  struct intlistlink *p = alloc_intlistlink ();

  p->datum = my_int;
  p->next = mylist;
  mylist = p;
}
```

The way to free the objects is by calling `free`. Here's a function to
free all the links in one of these lists:

``` C
void
free_intlist (struct intlistlink *p)
{
  while (p)
    {
      struct intlistlink *q = p;
      p = p->next;
      free (q);
    }
}
```

We must extract the `next` pointer from the object before freeing it,
because `free` can clobber the data that was in the object. For the same
reason, the program must not use the list any more after freeing its
elements. To make sure it won't, it is best to clear out the variable
where the list was stored, like this:

``` C
free_intlist (mylist);

mylist = NULL;
```

------------------------------------------------------------------------

Next: [Field Offset](Field-Offset.md), Previous: [Referencing
Structure Fields](Referencing-Fields.md), Up:
[Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
