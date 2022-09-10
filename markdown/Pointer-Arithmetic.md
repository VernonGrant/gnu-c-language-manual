Next: [Pointers and Arrays](Pointers-and-Arrays.md), Previous:
[Pointer Comparison](Pointer-Comparison.md), Up:
[Pointers](Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 14.10 Pointer Arithmetic 


Adding an integer (positive or negative) to a pointer is valid in C. It
assumes that the pointer points to an element in an array, and advances
or retracts the pointer across as many array elements as the integer
specifies. Here is an example, in which adding a positive integer
advances the pointer to a later element in the same array.

``` C
void
incrementing_pointers ()
{
  int array[5] = { 45, 29, 104, -3, 123456 };
  int elt0, elt1, elt4;

  int *p = &array[0];
  /* Now p points at element 0.  Fetch it.  */
  elt0 = *p;

  ++p;
  /* Now p points at element 1.  Fetch it.  */
  elt1 = *p;

  p += 3;
  /* Now p points at element 4 (the last).  Fetch it.  */
  elt4 = *p;

  printf ("elt0 %d  elt1 %d  elt4 %d.\n",
          elt0, elt1, elt4);
  /* Prints elt0 45  elt1 29  elt4 123456.  */
}
```

Here's an example where adding a negative integer retracts the pointer
to an earlier element in the same array.

``` C
void
decrementing_pointers ()
{
  int array[5] = { 45, 29, 104, -3, 123456 };
  int elt0, elt3, elt4;

  int *p = &array[4];
  /* Now p points at element 4 (the last).  Fetch it.  */
  elt4 = *p;

  --p;
  /* Now p points at element 3.  Fetch it.  */
  elt3 = *p;

  p -= 3;
  /* Now p points at element 0.  Fetch it.  */
  elt0 = *p;

  printf ("elt0 %d  elt3 %d  elt4 %d.\n",
          elt0, elt3, elt4);
  /* Prints elt0 45  elt3 -3  elt4 123456.  */
}
```

If one pointer value was made by adding an integer to another pointer
value, it should be possible to subtract the pointer values and recover
that integer. That works too in C.

``` C
void
subtract_pointers ()
{
  int array[5] = { 45, 29, 104, -3, 123456 };
  int *p0, *p3, *p4;

  int *p = &array[4];
  /* Now p points at element 4 (the last).  Save the value.  */
  p4 = p;

  --p;
  /* Now p points at element 3.  Save the value.  */
  p3 = p;

  p -= 3;
  /* Now p points at element 0.  Save the value.  */
  p0 = p;

  printf ("%d, %d, %d, %d\n",
          p4 - p0, p0 - p0, p3 - p0, p0 - p3);
  /* Prints 4, 0, 3, -3.  */
}
```

The addition operation does not know where arrays are. All it does is
add the integer (multiplied by object size) to the value of the pointer.
When the initial pointer and the result point into a single array, the
result is well-defined.

**Warning:** Only experts should do pointer arithmetic involving
pointers into different memory objects.

The difference between two pointers has type `int`, or `long` if
necessary (see [Integer Data Types](Integer-Types.md)). The clean way
to declare it is to use the typedef name `ptrdiff_t` defined in the file
`stddef.h`.

This definition of pointer subtraction is consistent with
pointer-integer addition, in that `(p3 - p1) + p1` equals `p3`, as in
ordinary algebra.

In standard C, addition and subtraction are not allowed on `void *`,
since the target type's size is not defined in that case. Likewise, they
are not allowed on pointers to function types. However, these operations
work in GNU C, and the "size of the target type" is taken as 1.

------------------------------------------------------------------------

Next: [Pointers and Arrays](Pointers-and-Arrays.md), Previous:
[Pointer Comparison](Pointer-Comparison.md), Up:
[Pointers](Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
