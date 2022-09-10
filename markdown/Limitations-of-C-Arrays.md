Next: [Multidimensional Arrays](Multidimensional-Arrays.md), Previous:
[Incomplete Array Types](Incomplete-Array-Types.md), Up:
[Arrays](Arrays.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 16.6 Limitations of C Arrays 


Arrays have quirks in C because they are not "first-class objects":
there is no way in C to operate on an array as a unit.

The other composite objects in C, structures and unions, are first-class
objects: a C program can copy a structure or union value in an
assignment, or pass one as an argument to a function, or make a function
return one. You can't do those things with an array in C. That is
because a value you can operate on never has an array type.

An expression in C can have an array type, but that doesn't produce the
array as a value. Instead it is converted automatically to a pointer to
the array's element at index zero. The code can operate on the pointer,
and through that on individual elements of the array, but it can't get
and operate on the array as a unit.

There are three exceptions to this conversion rule, but none of them
offers a way to operate on the array as a whole.

First, '`&`' applied to an expression with array type gives you
the address of the array, as an array type. However, you can't operate
on the whole array that way---if you apply '`*`' to get the
array back, that expression converts, as usual, to a pointer to its
zeroth element.

Second, the operators `sizeof`, `_Alignof`, and `typeof` do not convert
the array to a pointer; they leave it as an array. But they don't
operate on the array's data---they only give information about its type.

Third, a string constant used as an initializer for an array is not
converted to a pointer---rather, the declaration copies the *contents*
of that string in that one special case.

You *can* copy the contents of an array, just not with an assignment
operator. You can do it by calling the library function `memcpy` or
`memmove` (see [The GNU C
Library](https://www.gnu.org/software/libc/manual/html_node/Copying-and-Concatenation.md#Copying-and-Concatenation)
in The GNU C Library Reference Manual). Also, when a structure contains
just an array, you can copy that structure.

An array itself is an lvalue if it is a declared variable, or part of a
structure or union that is an lvalue. When you construct an array from
elements (see [Constructing Array
Values](Constructing-Array-Values.md)), that array is not an lvalue.

------------------------------------------------------------------------

Next: [Multidimensional Arrays](Multidimensional-Arrays.md), Previous:
[Incomplete Array Types](Incomplete-Array-Types.md), Up:
[Arrays](Arrays.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
