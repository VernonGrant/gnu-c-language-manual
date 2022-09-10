Next: [Calling Function Pointers](Calling-Function-Pointers.md),
Previous: [Declaring Function
Pointers](Declaring-Function-Pointers.md), Up: [Function
Pointers](Function-Pointers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 22.5.2 Assigning Function Pointers 


Assuming we have declared the variable `binary_op` as in the previous
section, giving it a value requires a suitable function to use. So let's
define a function suitable for the variable to point to. Here's one:

``` C
double
double_add (double a, double b)
{
  return a+b;
}
```

Now we can give it a value:

``` C
binary_op = double_add;
```

The target type of the function pointer must be upward compatible with
the type of the function (see [Compatible
Types](Compatible-Types.md)).

There is no need for '`&`' in front of `double_add`. Using a
function name such as `double_add` as an expression automatically
converts it to the function's address, with the appropriate function
pointer type. However, it is ok to use '`&`' if you feel that
is clearer:

``` C
binary_op = &double_add;
```
