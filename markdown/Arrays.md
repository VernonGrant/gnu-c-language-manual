Next: [Enumeration Types](Enumeration-Types.md), Previous:
[Structures](Structures.md), Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


## 16 Arrays 


An *array* is a data object that holds a series of *elements*, all of
the same data type. Each element is identified by its numeric
`index` within the array.

We presented arrays of numbers in the sample programs early in this
manual (see [An Example with Arrays](Array-Example.md)). However,
arrays can have elements of any data type, including pointers,
structures, unions, and other arrays.

If you know another programming language, you may suppose that you know
all about arrays, but C arrays have special quirks, so in this chapter
we collect all the information about arrays in C.

The elements of a C array are allocated consecutively in memory, with no
gaps between them. Each element is aligned as required for its data type
(see [Type Alignment](Type-Alignment.md)).

-   [Accessing Array Elements](Accessing-Array-Elements.md)
-   [Declaring an Array](Declaring-an-Array.md)
-   [Strings](Strings.md)
-   [Array Type Designators](Array-Type-Designators.md)
-   [Incomplete Array Types](Incomplete-Array-Types.md)
-   [Limitations of C Arrays](Limitations-of-C-Arrays.md)
-   [Multidimensional Arrays](Multidimensional-Arrays.md)
-   [Constructing Array Values](Constructing-Array-Values.md)
-   [Arrays of Variable Length](Arrays-of-Variable-Length.md)
