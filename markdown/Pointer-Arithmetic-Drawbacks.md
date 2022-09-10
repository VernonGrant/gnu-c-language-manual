Next: [Pointer-Integer Conversion](Pointer_002dInteger-Conversion.md),
Previous: [Pointer Increment and
Decrement](Pointer-Increment_002fDecrement.md), Up:
[Pointers](Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 14.14 Drawbacks of Pointer Arithmetic 


Pointer arithmetic is clean and elegant, but it is also the cause of a
major security flaw in the C language. Theoretically, it is only valid
to adjust a pointer within one object allocated as a unit in memory.
However, if you unintentionally adjust a pointer across the bounds of
the object and into some other object, the system has no way to detect
this error.

A bug which does that can easily result in clobbering part of another
object. For example, with `array[-1]` you can read or write the
nonexistent element before the beginning of an array---probably part of
some other data.

Combining pointer arithmetic with casts between pointer types, you can
create a pointer that fails to be properly aligned for its type. For
example,

``` C
int a[2];
char *pa = (char *)a;
int *p = (int *)(pa + 1);
```

gives `p` a value pointing to an "integer" that includes part of `a[0]`
and part of `a[1]`. Dereferencing that with `*p` can cause a fatal
`SIGSEGV` signal or it can return the contents of that badly aligned
`int` (see [Signals](Signals.md). If it "works," it may be quite slow.
It can also cause aliasing confusions (see [Aliasing](Aliasing.md)).

**Warning:** Using improperly aligned pointers is risky---don't do it
unless it is really necessary.
