Next: [The `main` Function](The-main-Function.md), Previous: [Function
Call Semantics](Function-Call-Semantics.md), Up:
[Functions](Functions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 22.5 Function Pointers 


A function name refers to a fixed function. Sometimes it is useful to
call a function to be determined at run time; to do this, you can use a
*function pointer value* that points to the chosen function (see
[Pointers](Pointers.md)).

Pointer-to-function types can be used to declare variables and other
data, including array elements, structure fields, and union
alternatives. They can also be used for function arguments and return
values. These types have the peculiarity that they are never converted
automatically to `void *` or vice versa. However, you can do that
conversion with a cast.

-   [Declaring Function Pointers](Declaring-Function-Pointers.md)
-   [Assigning Function Pointers](Assigning-Function-Pointers.md)
-   [Calling Function Pointers](Calling-Function-Pointers.md)
