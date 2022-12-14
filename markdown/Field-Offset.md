Next: [Structure Layout](Structure-Layout.md), Previous: [Dynamic
Memory Allocation](Dynamic-Memory-Allocation.md), Up:
[Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.4 Field Offset 


To determine the offset of a given field `field` in a
structure type `type`, use the macro `offsetof`, which is
defined in the file `stddef.h`. It is used like this:

``` C
offsetof (type, field)
```

Here is an example:

``` C
struct foo
{
  int element;
  struct foo *next;
};

offsetof (struct foo, next)
/* On most machines that is 4.  It may be 8.  */
```
