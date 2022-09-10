Previous: [Passing array arguments](Passing-Array-Args.md), Up:
[Arrays as Parameters](Arrays-as-Parameters.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 22.1.4.3 Type qualifiers on array parameters 

You can use the type qualifiers `const`, `restrict`, and `volatile` with
array parameters; for example:

``` C
void
clobber4 (volatile int array[20])
…
```

denotes that `array` is equivalent to a pointer to a volatile `int`.
Alternatively:

``` C
void
clobber4 (int array[const 20])
…
```

makes the array parameter equivalent to a constant pointer to an `int`.
If we want the `clobber4` function to succeed, it would not make sense
to write

``` C
void
clobber4 (const int array[20])
…
```

as this would tell the compiler that the parameter should point to an
array of constant `int` values, and then we would not be able to store
zeros in them.

In a function with multiple array parameters, you can use `restrict` to
tell the compiler that each array parameter passed in will be distinct:

``` C
void
foo (int array1[restrict 10], int array2[restrict 10])
…
```

Using `restrict` promises the compiler that callers will not pass in the
same array for more than one `restrict` array parameter. Knowing this
enables the compiler to perform better code optimization. This is the
same effect as using `restrict` pointers (see [`restrict`-Qualified
Pointers](restrict-Pointers.md)), but makes it clear when reading the
code that an array of a specific size is expected.
