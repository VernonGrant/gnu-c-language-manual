Next: [Type Rules for Aliasing](Aliasing-Type-Rules.md), Previous:
[Aliasing and Alignment](Aliasing-Alignment.md), Up:
[Aliasing](Aliasing.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### B.2 Aliasing and Length 

When converting a pointer to a different pointer type, make sure the
object it really points to is at least as long as the target of the
converted pointer. For instance, suppose `p` has type `int *` and it's
cast as follows:

``` C
int *p;

struct
  {
    double d, e, f;
  } foo;

struct foo *q = (struct foo *)p;

q->f = 5.14159;
```

the value `q->f` will run past the end of the `int` that `p` points to.
If `p` was initialized to the start of an array of type `int[6]`, the
object is long enough for three `double`s. But if `p` points to
something shorter, `q->f` will run on beyond the end of that, overlaying
some other data. Storing that will garble that other data. Or it could
extend past the end of memory space and cause a `SIGSEGV` signal (see
[Signals](Signals.md)).
