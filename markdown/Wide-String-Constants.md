Previous: [Wide Character Constants](Wide-Character-Constants.md), Up:
[Constants](Constants.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 12.11 Wide String Constants 


A *wide string constant* stands for an array of 16-bit or 32-bit
characters. They are rarely used; if you're just learning C, you may as
well skip this section.

There are three kinds of wide string constants, which differ in the data
type used for each character in the string. Each wide string constant is
equivalent to an array of integers, but the data type of those integers
depends on the kind of wide string. Using the constant in an expression
will convert the array to a pointer to its first element, as usual for
arrays in C (see [Accessing Array
Elements](Accessing-Array-Elements.md)). For each kind of wide string
constant, we state here what type that pointer will be.

`char16_t`

-   This is a 16-bit Unicode wide string constant: each element is a
    16-bit Unicode character code with type `char16_t`, so the string
    has the pointer type `char16_t *`. (That is a type designator; see
    [Pointer-Type Designators](Pointer-Type-Designators.md).) The
    constant is written as '`u`' (which must be lower case)
    followed (with no intervening space) by a string constant with the
    usual syntax.

`char32_t`

-   This is a 32-bit Unicode wide string constant: each element is a
    32-bit Unicode character code, and the string has type `char32_t *`.
    It's written as '`U`' (which must be upper case) followed
    (with no intervening space) by a string constant with the usual
    syntax.

`wchar_t`

-   This is the original kind of wide string constant. It's written as
    '`L`' (which must be upper case) followed (with no
    intervening space) by a string constant with the usual syntax, and
    the string has type `wchar_t *`.

    The width of the data type `wchar_t` depends on the target platform,
    which makes this kind of wide string somewhat less useful than the
    newer kinds.

`char16_t` and `char32_t` are declared in the header file
`uchar.h`. `wchar_t` is declared in `stddef.h`.

Consecutive wide string constants of the same kind concatenate, just
like ordinary string constants. A wide string constant concatenated with
an ordinary string constant results in a wide string constant. You can't
concatenate two wide string constants of different kinds. In addition,
you can't concatenate a wide string constant (of any kind) with a UTF-8
string constant.

------------------------------------------------------------------------

Previous: [Wide Character Constants](Wide-Character-Constants.md), Up:
[Constants](Constants.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
