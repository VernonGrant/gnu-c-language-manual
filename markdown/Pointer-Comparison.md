Next: [Pointer Arithmetic](Pointer-Arithmetic.md), Previous: [Void
Pointers](Void-Pointers.md), Up: [Pointers](Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 14.9 Pointer Comparison 


Two pointer values are equal if they point to the same location, or if
they are both null. You can test for this with `==` and `!=`. Here's a
trivial example:

``` C
{
  int i;
  int *p, *q;

  p = &i;
  q = &i;
  if (p == q)
    printf ("This will be printed.\n");
  if (p != q)
    printf ("This won't be printed.\n");
}
```

Ordering comparisons such as `>` and `>=` operate on pointers by
converting them to unsigned integers. The C standard says the two
pointers must point within the same object in memory, but on GNU/Linux
systems these operations simply compare the numeric values of the
pointers.

The pointer values to be compared should in principle have the same
type, but they are allowed to differ in limited cases. First of all, if
the two pointers' target types are nearly compatible (see [Compatible
Types](Compatible-Types.md)), the comparison is allowed.

If one of the operands is `void *` (see [Void
Pointers](Void-Pointers.md)) and the other is another pointer type,
the comparison operator converts the `void *` pointer to the other type
so as to compare them. (In standard C, this is not allowed if the other
type is a function pointer type, but that works in GNU C.)

Comparison operators also allow comparing the integer 0 with a pointer
value. Thus works by converting 0 to a null pointer of the same type as
the other operand.
