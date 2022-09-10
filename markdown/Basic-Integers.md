Next: [Signed and Unsigned Types](Signed-and-Unsigned-Types.md), Up:
[Integer Data Types](Integer-Types.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 11.1.1 Basic Integers 


Integer data types in C can be signed or unsigned. An unsigned type can
represent only positive numbers and zero. A signed type can represent
both positive and negative numbers, in a range spread almost equally on
both sides of zero.

Aside from signedness, the integer data types vary in size: how many
bytes long they are. The size determines how many different integer
values the type can hold.

Here's a list of the signed integer data types, with the sizes they have
on most computers. Each has a corresponding unsigned type; see [Signed
and Unsigned Types](Signed-and-Unsigned-Types.md).

`signed char`

-   One byte (8 bits). This integer type is used mainly for integers
    that represent characters, as part of arrays or other data
    structures.

`short`\
`short int`

-   Two bytes (16 bits).

`int`

-   Four bytes (32 bits).

`long`\
`long int`

-   Four bytes (32 bits) or eight bytes (64 bits), depending on the
    platform. Typically it is 32 bits on 32-bit computers and 64 bits on
    64-bit computers, but there are exceptions.

`long long`\
`long long int`

-   Eight bytes (64 bits). Supported in GNU C in the 1980s, and
    incorporated into standard C as of ISO C99.

You can omit `int` when you use `long` or `short`. This is harmless and
customary.
