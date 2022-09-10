Next: [Cast to a Union Type](Cast-to-Union.md), Previous:
[Unions](Unions.md), Up: [Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.14 Packing With Unions 

Sometimes we design a union with the intention of packing various kinds
of objects into a certain amount of memory space. For example.

``` C
union bytes8
{
  long long big_int_elt;
  double double_elt;
  struct { int first, second; } two_ints;
  struct { void *first, *second; } two_ptrs;
};

union bytes8 *p;
```

This union makes it possible to look at 8 bytes of data that `p` points
to as a single 8-byte integer (`p->big_int_elt`), as a single
floating-point number (`p->double_elt`), as a pair of integers
(`p->two_ints.first` and `p->two_ints.second`), or as a pair of pointers
(`p->two_ptrs.first` and `p->two_ptrs.second`).

To pack storage with such a union makes assumptions about the sizes of
all the types involved. This particular union was written expecting a
pointer to have the same size as `int`. On a machine where one pointer
takes 8 bytes, the code using this union probably won't work as
expected. The union, as such, will function correctly---if you store two
values through `two_ints` and extract them through `two_ints`, you will
get the same integers back---but the part of the program that expects
the union to be 8 bytes long could malfunction, or at least use too much
space.

The above example shows one case where a `struct` type with no tag can
be useful. Another way to get effectively the same result is with arrays
as members of the union:

``` C
union eight_bytes
{
  long long big_int_elt;
  double double_elt;
  int two_ints[2];
  void *two_ptrs[2];
};
```
