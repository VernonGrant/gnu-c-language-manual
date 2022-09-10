Next: [Null Pointers](Null-Pointers.md), Previous: [Pointer-Type
Designators](Pointer-Type-Designators.md), Up:
[Pointers](Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 14.5 Dereferencing Pointers 


The main use of a pointer value is to *dereference it* (access the data
it points at) with the unary '`*`' operator. For instance,
`*&i` is the value at `i`'s address---which is just `i`. The two
expressions are equivalent, provided `&i` is valid.

A pointer-dereference expression whose type is data (not a function) is
an lvalue.

Pointers become really useful when we store them somewhere and use them
later. Here's a simple example to illustrate the practice:

``` C
{
  int i;
  int *ptr;

  ptr = &i;

  i = 5;

  …
  
  return *ptr;   /* Returns 5, fetched from i.  */
}
```

This shows how to declare the variable `ptr` as type `int *` (pointer to
`int`), store a pointer value into it (pointing at `i`), and use it
later to get the value of the object it points at (the value in `i`).

If anyone can provide a useful example which is this basic, I would be
grateful.
