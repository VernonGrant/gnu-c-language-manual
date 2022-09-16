Next: [Other Data Types](Other-Data-Types.md), Previous: [Complex Data
Types](Complex-Data-Types.md), Up: [Primitive Data
Types](Primitive-Types.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 11.4 The Void Type 


The data type `void` is a dummy---it allows no operations. It really
means "no value at all." When a function is meant to return no value, we
write `void` for its return type. Then `return` statements in that
function should not specify a value (see [`return`
Statement](return-Statement.md)). Here's an example:

``` C
void
print_if_positive (double x, double y)
{
  if (x <= 0)
    return;
  if (y <= 0)
    return;
  printf ("Next point is (%f,%f)\n", x, y);
}
```

A `void`-returning function is comparable to what some other languages
(for instance, Fortran and Pascal) call a "procedure" instead of a
"function."
