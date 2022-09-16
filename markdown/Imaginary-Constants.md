Next: [Invalid Numbers](Invalid-Numbers.md), Previous: [Floating-Point
Constants](Floating-Constants.md), Up: [Constants](Constants.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 12.4 Imaginary Constants 


A complex number consists of a real part plus an imaginary part. (You
may omit one part if it is zero.) This section explains how to write
numeric constants with imaginary values. By adding these to ordinary
real-valued numeric constants, we can make constants with complex
values.

The simple way to write an imaginary-number constant is to attach the
suffix '`i`' or '`I`', or '`j`' or
'`J`', to an integer or floating-point constant. For example,
`2.5fi` has type `_Complex float` and `3i` has type `_Complex int`. The
four alternative suffix letters are all equivalent.


The other way to write an imaginary constant is to multiply a real
constant by `_Complex_I`, which represents the imaginary number i.
Standard C doesn't support suffixing with '`i`' or
'`j`', so this clunky method is needed.

To write a complex constant with a nonzero real part and a nonzero
imaginary part, write the two separately and add them, like this:

``` C
4.0 + 3.0i
```

That gives the value 4 + 3i, with type `_Complex double`.

Such a sum can include multiple real constants, or none. Likewise, it
can include multiple imaginary constants, or none. For example:

``` C
_Complex double foo, bar, quux;

foo = 2.0i + 4.0 + 3.0i; /* Imaginary part is 5.0. */
bar = 4.0 + 12.0; /* Imaginary part is 0.0. */
quux = 3.0i + 15.0i; /* Real part is 0.0. */
```

See [Complex Data Types](Complex-Data-Types.md).
