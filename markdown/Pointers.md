Next: [Structures](Structures.md), Previous: [Type
Size](Type-Size.md), Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


## 14 Pointers 


Among high-level languages, C is rather low level, close to the machine.
This is mainly because it has explicit *pointers*. A pointer value is
the numeric address of data in memory. The type of data to be found at
that address is specified by the data type of the pointer itself. The
unary operator '`*`' gets the data that a pointer points
to---this is called *dereferencing the pointer*.

C also allows pointers to functions, but since there are some
differences in how they work, we treat them later. See [Function
Pointers](Function-Pointers.md).

-   [Address of Data](Address-of-Data.md)
-   [Pointer Types](Pointer-Types.md)
-   [Pointer-Variable Declarations](Pointer-Declarations.md)
-   [Pointer-Type Designators](Pointer-Type-Designators.md)
-   [Dereferencing Pointers](Pointer-Dereference.md)
-   [Null Pointers](Null-Pointers.md)
-   [Dereferencing Null or Invalid Pointers](Invalid-Dereference.md)
-   [Void Pointers](Void-Pointers.md)
-   [Pointer Comparison](Pointer-Comparison.md)
-   [Pointer Arithmetic](Pointer-Arithmetic.md)
-   [Pointers and Arrays](Pointers-and-Arrays.md)
-   [Pointer Arithmetic at Low Level](Pointer-Arithmetic-Low-Level.md)
-   [Pointer Increment and
    Decrement](Pointer-Increment_002fDecrement.md)
-   [Drawbacks of Pointer Arithmetic](Pointer-Arithmetic-Drawbacks.md)
-   [Pointer-Integer Conversion](Pointer_002dInteger-Conversion.md)
-   [Printing Pointers](Printing-Pointers.md)
