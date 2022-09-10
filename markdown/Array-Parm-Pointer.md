Next: [Passing array arguments](Passing-Array-Args.md), Up: [Arrays as
Parameters](Arrays-as-Parameters.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 22.1.4.1 Array parameters are pointers 

Declaring a function parameter variable as an array really gives it a
pointer type. C does this because an expression with array type, if used
as an argument in a function call, is converted automatically to a
pointer (to the zeroth element of the array). If you declare the
corresponding parameter as an "array", it will work correctly with the
pointer value that really gets passed.

This relates to the fact that C does not check array bounds in access to
elements of the array (see [Accessing Array
Elements](Accessing-Array-Elements.md)).

For example, in this function,

``` C
void
clobber4 (int array[20])
{
  array[4] = 0;
}
```

the parameter `array`'s real type is `int *`; the specified length, 20,
has no effect on the program. You can leave out the length and write
this:

``` C
void
clobber4 (int array[])
{
  array[4] = 0;
}
```

or write the parameter declaration explicitly as a pointer:

``` C
void
clobber4 (int *array)
{
  array[4] = 0;
}
```

They are all equivalent.
