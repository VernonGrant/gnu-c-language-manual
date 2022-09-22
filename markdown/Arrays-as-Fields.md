Next: [Dynamic Memory Allocation](Dynamic-Memory-Allocation.md),
Previous: [Referencing Structure Fields](Referencing-Fields.md), Up:
[Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.2 Arrays as Fields 

When you declare field in a structure as an array, as here:

``` C
struct record
  {
    char *name;
    int data[4];
  };
```

Each `struct record` object holds one string (a pointer, of course) and
four integers, all part of a field called `data`. If `recptr` is a
pointer of type `struct record *`, then it points to a `struct record`
which contains those things; you can access the second integer in that
record with `recptr->data[1]`.

If you have two objects of type `struct record`, each one contains an
array. With this declaration,

``` C
struct record r1, r2;
```

`r1.data` holds space for 4 `int`s, and `r2.data` holds space for
another 4 `int`s,
