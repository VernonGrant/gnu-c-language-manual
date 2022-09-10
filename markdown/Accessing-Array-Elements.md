Next: [Declaring an Array](Declaring-an-Array.md), Up:
[Arrays](Arrays.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 16.1 Accessing Array Elements 


If the variable `a` is an array, the `n`{.variable}th element of `a` is
`a[n]`. You can use that expression to access an element's value or to
assign to it:

``` C
x = a[5];
a[6] = 1;
```

Since the variable `a` is an lvalue, `a[n]` is also an lvalue.

The lowest valid index in an array is 0, *not* 1, and the highest valid
index is one less than the number of elements.

The C language does not check whether array indices are in bounds, so if
the code uses an out-of-range index, it will access memory outside the
array.

**Warning:** Using only valid index values in C is the programmer's
responsibility.

Array indexing in C is not a primitive operation: it is defined in terms
of pointer arithmetic and dereferencing. Now that we know *what* `a[i]`
does, we can ask *how* `a[i]` does its job.

In C, `x[y]` is an abbreviation for `*(x+y)`. Thus, `a[i]` really means
`*(a+i)`. See [Pointers and Arrays](Pointers-and-Arrays.md).

When an expression with array type (such as `a`) appears as part of a
larger C expression, it is converted automatically to a pointer to
element zero of that array. For instance, `a` in an expression is
equivalent to `&a[0]`. Thus, `*(a+i)` is computed as `*(&a[0]+i)`.

Now we can analyze how that expression gives us the desired element of
the array. It makes a pointer to element 0 of `a`, advances it by the
value of `i`, and dereferences that pointer.

Another equivalent way to write the expression is `(&a[0])[i]`.

------------------------------------------------------------------------

Next: [Declaring an Array](Declaring-an-Array.md), Up:
[Arrays](Arrays.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
