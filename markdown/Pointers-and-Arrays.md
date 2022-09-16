Next: [Pointer Arithmetic at
Low-Level](Low_002dLevel-Pointer-Arithmetic.md), Previous: [Pointer
Arithmetic](Pointer-Arithmetic.md), Up: [Pointers](Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 14.11 Pointers and Arrays 


The clean way to refer to an array element is `array[index]`. Another,
complicated way to do the same job is to get the address of that element
as a pointer, then dereference it: `* (&array[0] + index)` (or
equivalently `* (array + index)`). This first gets a pointer to element
zero, then increments it with `+` to point to the desired element, then
gets the value from there.

That pointer-arithmetic construct is the *definition* of square brackets
in C. `a[b]` means, by definition, `*(a + b)`. This definition uses
`a` and `b` symmetrically, so one must be a
pointer and the other an integer; it does not matter which comes first.

Since indexing with square brackets is defined in terms of addition and
dereferencing, that too is symmetrical. Thus, you can write `3[array]`
and it is equivalent to `array[3]`. However, it would be foolish to
write `3[array]`, since it has no advantage and could confuse people who
read the code.

It may seem like a discrepancy that the definition `*(a + b)` requires a
pointer, while `array[3]` uses an array value instead. Why is this
valid? The name of the array, when used by itself as an expression
(other than in `sizeof`), stands for a pointer to the array's zeroth
element. Thus, `array + 3` converts `array` implicitly to `&array[0]`,
and the result is a pointer to element 3, equivalent to `&array[3]`.

Since square brackets are defined in terms of such an addition,
`array[3]` first converts `array` to a pointer. That's why it works to
use an array directly in that construct.

------------------------------------------------------------------------

Next: [Pointer Arithmetic at
Low-Level](Low_002dLevel-Pointer-Arithmetic.md), Previous: [Pointer
Arithmetic](Pointer-Arithmetic.md), Up: [Pointers](Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
