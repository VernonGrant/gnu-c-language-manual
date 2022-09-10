Next: [Assignment Type Conversions](Assignment-Type-Conversions.md),
Up: [Type Conversions](Type-Conversions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 24.1 Explicit Type Conversion 


You can do explicit conversions using the unary *cast* operator, which
is written as a type designator (see [Type
Designators](Type-Designators.md)) in parentheses. For example,
`(int)` is the operator to cast to type `int`. Here's an example of
using it:

``` C
{
  double d = 5.5;

  printf ("Floating point value: %f\n", d);
  printf ("Rounded to integer: %d\n", (int) d);
}
```

Using `(int) d` passes an `int` value as argument to `printf`, so you
can print it with '`%d`'. Using just `d` without the cast would
pass the value as `double`. That won't work at all with '`%d`';
the results would be gibberish.

To divide one integer by another without rounding, cast either of the
integers to `double` first:

``` C
(double) dividend / divisor
dividend / (double) divisor
```

It is enough to cast one of them, because that forces the common type to
`double` so the other will be converted automatically.

The valid cast conversions are:

-   One numerical type to another.
-   One pointer type to another. (Converting between pointers that point
    to functions and pointers that point to data is not standard C.)
-   A pointer type to an integer type.
-   An integer type to a pointer type.
-   To a union type, from the type of any alternative in the union (see
    [Unions](Unions.md)). (This is a GNU extension.)
-   Anything, to `void`.
