Next: [Overlaying Different Structures](Overlaying-Structures.md),
Previous: [Arrays of Length Zero](Zero-Length.md), Up:
[Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.11 Flexible Array Fields 


The C99 standard adopted a more complex equivalent of zero-length array
fields. It's called a *flexible array*, and it's indicated by omitting
the length, like this:

``` C
struct line
{
  int length;
  char contents[];
};
```

The flexible array has to be the last field in the structure, and there
must be other fields before it.

Under the C standard, a structure with a flexible array can't be part of
another structure, and can't be an element of an array.

GNU C allows static initialization of flexible array fields. The effect
is to "make the array long enough" for the initializer.

``` C
struct f1 { int x; int y[]; } f1
  = { 1, { 2, 3, 4 } };
```

This defines a structure variable named `f1` whose type is `struct f1`.
In C, a variable name or function name never conflicts with a structure
type tag.

Omitting the flexible array field's size lets the initializer determine
it. This is allowed only when the flexible array is defined in the
outermost structure and you declare a variable of that structure type.
For example:

``` C
struct foo { int x; int y[]; };
struct bar { struct foo z; };

struct foo a = { 1, { 2, 3, 4 } };        // Valid.
struct bar b = { { 1, { 2, 3, 4 } } };    // Invalid.
struct bar c = { { 1, { } } };            // Valid.
struct foo d[1] = { { 1 { 2, 3, 4 } } };  // Invalid.
```
