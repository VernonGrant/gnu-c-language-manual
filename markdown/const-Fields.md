Next: [Arrays of Length Zero](Zero-Length.md), Previous: [Bit Field
Packing](Bit-Field-Packing.md), Up: [Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.9 `const` Fields 


A structure field declared `const` cannot be assigned to (see [`const`
Variables and Fields](const.md)). For instance, let's define this
modified version of `struct intlistlink`:

``` C
struct intlistlink_ro  /* “ro” for read-only.  */
  {
    const int datum;
    struct intlistlink *next;
  };
```

This structure can be used to prevent part of the code from modifying
the `datum` field:

``` C
/* p has type struct intlistlink *.
   Convert it to struct intlistlink_ro *.  */
struct intlistlink_ro *q
  = (struct intlistlink_ro *) p;

q->datum = 5;     /* Error! */
p->datum = 5;     /* Valid since *p is
                     not a struct intlistlink_ro.  */
```

A `const` field can get a value in two ways: by initialization of the
whole structure, and by making a pointer-to-structure point to an object
in which that field already has a value.

Any `const` field in a structure type makes assignment impossible for
structures of that type (see [Structure
Assignment](Structure-Assignment.md)). That is because structure
assignment works by assigning the structure's fields, one by one.
