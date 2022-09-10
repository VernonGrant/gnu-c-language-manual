Next: [Pointers](Pointers.md), Previous: [Constants](Constants.md),
Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


## 13 Type Size 


Each data type has a *size*, which is the number of bytes (see [Storage
and Data](Storage.md)) that it occupies in memory. To refer to the
size in a C program, use `sizeof`. There are two ways to use it:

`sizeof expression`

-   This gives the size of `expression`{.variable}, based on its data
    type. It does not calculate the value of `expression`{.variable},
    only its size, so if `expression`{.variable} includes side effects
    or function calls, they do not happen. Therefore, `sizeof` is always
    a compile-time operation that has zero run-time cost.

    A value that is a bit field (see [Bit Fields](Bit-Fields.md)) is
    not allowed as an operand of `sizeof`.

    For example,

    
    ``` C
    double a;

    i = sizeof a + 10;
    ```
    

    sets `i` to 18 on most computers because `a` occupies 8 bytes.

    Here's how to determine the number of elements in an array `array`:

    
    ``` C
    (sizeof array / sizeof array[0])
    ```
    

    The expression `sizeof array` gives the size of the array, not the
    size of a pointer to an element. However, if `expression`{.variable}
    is a function parameter that was declared as an array, that variable
    really has a pointer type (see [Array parameters are
    pointers](Array-Parm-Pointer.md)), so the result is the size of
    that pointer.

`sizeof (type)`

-   This gives the size of `type`{.variable}. For example,

    
    ``` C
    i = sizeof (double) + 10;
    ```
    

    is equivalent to the previous example.

    You can't apply `sizeof` to an incomplete type (see [Incomplete
    Types](Incomplete-Types.md)), nor `void`. Using it on a function
    type gives 1 in GNU C, which makes adding an integer to a function
    pointer work as desired (see [Pointer
    Arithmetic](Pointer-Arithmetic.md)).

**Warning**: When you use `sizeof` with a type instead of an expression,
you must write parentheses around the type.

**Warning**: When applying `sizeof` to the result of a cast (see
[Explicit Type Conversion](Explicit-Type-Conversion.md)), you must
write parentheses around the cast expression to avoid an ambiguity in
the grammar of C. Specifically,

``` C
sizeof (int) -x
```

parses as

``` C
(sizeof (int)) - x
```

If what you want is

``` C
sizeof ((int) -x)
```

you must write it that way, with parentheses.

The data type of the value of the `sizeof` operator is always one of the
unsigned integer types; which one of those types depends on the machine.
The header file `stddef.h` defines the typedef name `size_t` as an alias
for this type. See [Defining Typedef
Names](Defining-Typedef-Names.md).

------------------------------------------------------------------------

Next: [Pointers](Pointers.md), Previous: [Constants](Constants.md),
Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
