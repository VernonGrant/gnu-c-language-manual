Previous: [Integer Representations](Integer-Representations.md), Up:
[Integers in Depth](Integers-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 27.2 Maximum and Minimum Values 


For each primitive integer type, there is a standard macro defined in
`limits.h` that gives the largest value that type can hold. For
instance, for type `int`, the maximum value is `INT_MAX`. On a 32-bit
computer, that is equal to 2,147,483,647. The maximum value for
`unsigned int` is `UINT_MAX`, which on a 32-bit computer is equal to
4,294,967,295. Likewise, there are `SHRT_MAX`, `LONG_MAX`, and
`LLONG_MAX`, and corresponding unsigned limits `USHRT_MAX`, `ULONG_MAX`,
and `ULLONG_MAX`.

Since there are three ways to specify a `char` type, there are also
three limits: `CHAR_MAX`, `SCHAR_MAX`, and `UCHAR_MAX`.

For each type that is or might be signed, there is another symbol that
gives the minimum value it can hold. (Just replace `MAX` with `MIN` in
the names listed above.) There is no minimum limit symbol for types
specified with `unsigned` because the minimum for them is universally
zero.

`INT_MIN` is not the negative of `INT_MAX`. In two's-complement
representation, the most negative number is 1 less than the negative of
the most positive number. Thus, `INT_MIN` on a 32-bit computer has the
value -2,147,483,648. You can't actually write the value that way in C,
since it would overflow. That's a good reason to use `INT_MIN` to
specify that value. Its definition is written to avoid overflow.

This is part of the GNU C Intro and Reference Manual and covered by its
license.
