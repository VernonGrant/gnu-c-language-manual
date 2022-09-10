Next: [Dereferencing Null or Invalid
Pointers](Invalid-Dereference.md), Previous: [Dereferencing
Pointers](Pointer-Dereference.md), Up: [Pointers](Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 14.6 Null Pointers 


A pointer value can be *null*, which means it does not point to any
object. The cleanest way to get a null pointer is by writing `NULL`, a
standard macro defined in `stddef.h`. You can also do it by
casting 0 to the desired pointer type, as in `(char *) 0`. (The cast
operator performs explicit type conversion; See [Explicit Type
Conversion](Explicit-Type-Conversion.md).)

You can store a null pointer in any lvalue whose data type is a pointer
type:

``` C
char *foo;
foo = NULL;
```

These two, if consecutive, can be combined into a declaration with
initializer,

``` C
char *foo = NULL;
```

You can also explicitly cast `NULL` to the specific pointer type you
want---it makes no difference.

``` C
char *foo;
foo = (char *) NULL;
```

To test whether a pointer is null, compare it with zero or `NULL`, as
shown here:

``` C
if (p != NULL)
  /* p is not null.  */
  operate (p);
```

Since testing a pointer for not being null is basic and frequent, all
but beginners in C will understand the conditional without need for
`!= NULL`:

``` C
if (p)
  /* p is not null.  */
  operate (p);
```
