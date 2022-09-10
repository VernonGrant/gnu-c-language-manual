Previous: [Label Value Uses](Label-Value-Uses.md), Up: [Labels as
Values](Labels-as-Values.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 19.14.2 Label Value Caveats 

Jumping to a label defined in another function does not work. It can
cause unpredictable results.

The best way to avoid this is to store label values only in automatic
variables, or static variables whose names are declared within the
function. Never pass them as arguments.


An optimization known as *cloning* generates multiple simplified
variants of a function's code, for use with specific fixed arguments.
Using label values in certain ways, such as saving the address in one
call to the function and using it again in another call, would make
cloning give incorrect results. These functions must disable cloning.

Inlining calls to the function would also result in multiple copies of
the code, each with its own value of the same label. Using the label in
a computed goto is no problem, because the computed goto inhibits
inlining. However, using the label value in some other way, such as an
indication of where an error occurred, would be optimized wrong. These
functions must disable inlining.

To prevent inlining or cloning of a function, specify
`__attribute__((__noinline__,__noclone__))` in its definition. See
[Attributes in Declarations](Attributes.md).

When a function uses a label value in a static variable initializer,
that automatically prevents inlining or cloning the function.
