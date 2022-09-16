Next: [Conversion among Integer Types](Integer-Conversion.md),
Previous: [Signed and Unsigned Types](Signed-and-Unsigned-Types.md),
Up: [Integer Data Types](Integer-Types.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 11.1.3 Narrow Integers 

The types that are narrower than `int` are rarely used for ordinary
variables---we declare them `int` instead. This is because C converts
those narrower types to `int` for any arithmetic. There is literally no
reason to declare a local variable `char`, for instance.

In particular, if the value is really a character, you should declare
the variable `int`. Not `char`! Using that narrow type can force the
compiler to truncate values for conversion, which is a waste.
Furthermore, some functions return either a character value, or -1 for
"no character." Using `int` makes it possible to distinguish -1 from a
character by sign.

The narrow integer types are useful as parts of other objects, such as
arrays and structures. Compare these array declarations, whose sizes on
32-bit processors are shown:

``` C
signed char ac[1000];   /* 1000 bytes */
short as[1000];         /* 2000 bytes */
int ai[1000];           /* 4000 bytes */
long long all[1000];    /* 8000 bytes */
```

In addition, character strings must be made up of `char`s, because
that's what all the standard library string functions expect. Thus,
array `ac` could be used as a character string, but the others could not
be.
