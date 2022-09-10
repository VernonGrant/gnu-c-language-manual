Previous: [Declaring Arrays and
Pointers](Declaring-Arrays-and-Pointers.md), Up: [Variable
Declarations](Variable-Declarations.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 20.1.2 Combining Variable Declarations 


When multiple declarations have the same `keywords` and
`basetype`, you can combine them using commas. Thus,

``` C
keywords basetype
   decorated-variable-1 [= init1],
   decorated-variable-2 [= init2];
```

is equivalent to

``` C
keywords basetype
   decorated-variable-1 [= init1];
keywords basetype
   decorated-variable-2 [= init2];
```

Here are some simple examples:

``` C
int a, b;
int a = 1, b = 2;
int a, *p, array[5];
int a = 0, *p = &a, array[5] = {1, 2};
```

In the last two examples, `a` is an `int`, `p` is a pointer to `int`,
and `array` is an array of 5 `int`s. Since the initializer for `array`
specifies only two elements, the other three elements are initialized to
zero.
