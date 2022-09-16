Previous: [Assigning Function
Pointers](Assigning-Function-Pointers.md), Up: [Function
Pointers](Function-Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 22.5.3 Calling Function Pointers 


To call the function specified by a function pointer, just write the
function pointer value in a function call. For instance, here's a call
to the function `binary_op` points to:

``` C
binary_op (x, 5)
```

Since the data type of `binary_op` explicitly specifies type `double`
for the arguments, the call converts `x` and 5 to `double`.

The call conceptually dereferences the pointer `binary_op` to "get" the
function it points to, and calls that function. If you wish, you can
explicitly represent the dereference by writing the `*` operator:

``` C
(*binary_op) (x, 5)
```

The '`*`' reminds people reading the code that `binary_op` is a
function pointer rather than the name of a specific function.
