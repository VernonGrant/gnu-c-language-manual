Next: [Local Variables](Local-Variables.md), Previous: [Designated
Initializers](Designated-Inits.md), Up: [Variables](Variables.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 20.4 Referring to a Type with `__auto_type` 


You can declare a variable copying the type from the initializer by
using `__auto_type` instead of a particular type. Here's an example:

``` C
#define max(a,b) \
  ({ __auto_type _a = (a); \
      __auto_type _b = (b); \
    _a > _b ? _a : _b })
```

This defines `_a` to be of the same type as `a`, and `_b` to be of the
same type as `b`. This is a useful thing to do in a macro that ought to
be able to handle any type of data (see [Using `__auto_type` for Local
Variables](Macros-and-Auto-Type.md)).

The original GNU C method for obtaining the type of a value is to use
`typeof`, which takes as an argument either a value or the name of a
type. The previous example could also be written as:

``` C
#define max(a,b) \
  ({ typeof(a) _a = (a); \
      typeof(b) _b = (b); \
    _a > _b ? _a : _b })
```

`typeof` is more flexible than `__auto_type`; however, the principal use
case for `typeof` is in variable declarations with initialization, which
is exactly what `__auto_type` handles.
