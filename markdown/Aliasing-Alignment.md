Next: [Aliasing and Length](Aliasing-Length.md), Up:
[Aliasing](Aliasing.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### B.1 Aliasing and Alignment 

In order for a type-converted pointer to be valid, it must have the
alignment that the new pointer type requires. For instance, on most
computers, `int` has alignment 4; the address of an `int` must be a
multiple of 4. However, `char` has alignment 1, so the address of a
`char` is usually not a multiple of 4. Taking the address of such a
`char` and casting it to `int *` probably results in an invalid pointer.
Trying to dereference it may cause a `SIGBUS` signal, depending on the
platform in use (see [Signals](Signals.md)).

``` C
foo ()
{
  char i[4];
  int *p = (int *) &i[1]; /* Misaligned pointer! */
  return *p;              /* Crash! */
}
```

This requirement is never a problem when casting the return value of
`malloc` because that function always returns a pointer with as much
alignment as any type can require.
