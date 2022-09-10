Next: [Limitations of C Arrays](Limitations-of-C-Arrays.md), Previous:
[Array Type Designators](Array-Type-Designators.md), Up:
[Arrays](Arrays.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 16.5 Incomplete Array Types 


An array is equivalent, for most purposes, to a pointer to its zeroth
element. When that is true, the length of the array is irrelevant. The
length needs to be known only for allocating space for the array, or for
`sizeof` and `typeof` (see [Referring to a Type with
`__auto_type`](Auto-Type.md)). Thus, in some contexts C allows

-   An `extern` declaration says how to refer to a variable allocated
    elsewhere. It does not need to allocate space for the variable, so
    if it is an array, you can omit the length. For example,
    
    ``` C
    extern int foo[];
    ```
    
-   When declaring a function parameter as an array, the argument value
    passed to the function is really a pointer to the array's zeroth
    element. This value does not say how long the array really is, there
    is no need to declare it. For example,
    
    ``` C
    int
    func (int foo[])
    ```
    

These declarations are examples of *incomplete* array types, types that
are not fully specified. The incompleteness makes no difference for
accessing elements of the array, but it matters for some other things.
For instance, `sizeof` is not allowed on an incomplete type.

With multidimensional arrays, only the first dimension can be omitted:

``` C
extern struct chesspiece *funnyboard foo[][8];
```

In other words, the code doesn't have to say how many rows there are,
but it must state how big each row is.
