Next: [`restrict` Pointer Example](restrict-Pointer-Example.md),
Previous: [`volatile` Variables and Fields](volatile.md), Up: [Type
Qualifiers](Type-Qualifiers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 21.3 `restrict`-Qualified Pointers 


You can declare a pointer as "restricted" using the `restrict` type
qualifier, like this:

``` C
int *restrict p = x;
```

This enables better optimization of code that uses the pointer.

If `p` is declared with `restrict`, and then the code references the
object that `p` points to (using `*p` or `p[i]`), the `restrict`
declaration promises that the code will not access that object in any
other way---only through `p`.

For instance, it means the code must not use another pointer to access
the same space, as shown here:

``` C
int *restrict p = whatever;
int *q = p;
foo (*p, *q);
```

That contradicts the `restrict` promise by accessing the object that `p`
points to using `q`, which bypasses `p`. Likewise, it must not do this:

``` C
int *restrict p = whatever;
struct { int *a, *b; } s;
s.a = p;
foo (*p, *s.a);
```

This example uses a structure field instead of the variable `q` to hold
the other pointer, and that contradicts the promise just the same.

The keyword `restrict` also promises that `p` won't point to the
allocated space of any automatic or static variable. So the code must
not do this:

``` C
int a;
int *restrict p = &a;
foo (*p, a);
```

because that does direct access to the object (`a`) that `p` points to,
which bypasses `p`.

If the code makes such promises with `restrict` then breaks them,
execution is unpredictable.
