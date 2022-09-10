Next: [Functions That Accept Structure
Arguments](Structs-as-Parameters.md), Previous: [Static
Functions](Static-Functions.md), Up: [Function
Definitions](Function-Definitions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 22.1.4 Arrays as Parameters 


Arrays in C are not first-class objects: it is impossible to copy them.
So they cannot be passed as arguments like other values. See
[Limitations of C Arrays](Limitations-of-C-Arrays.md). Rather, array
parameters work in a special way.

-   [Array parameters are pointers](Array-Parm-Pointer.md)
-   [Passing array arguments](Passing-Array-Args.md)
-   [Type qualifiers on array parameters](Array-Parm-Qualifiers.md)
