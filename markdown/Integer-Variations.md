Previous: [Boolean Type](Boolean-Type.md), Up: [Integer Data
Types](Integer-Types.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 11.1.6 Integer Variations 

The integer types of C have standard *names*, but what they *mean*
varies depending on the kind of platform in use: which kind of computer,
which operating system, and which compiler. It may even depend on the
compiler options used.

Plain `char` may be signed or unsigned; this depends on the platform,
too. Even for GNU C, there is no general rule.

In theory, all of the integer types' sizes can vary. `char` is always
considered one "byte" for C, but it is not necessarily an 8-bit byte; on
some platforms it may be more than 8 bits. ISO C specifies only that
none of these types is narrower than the ones above it in the list in
[Basic Integers](Basic-Integers.md), and that `short` has at least 16
bits.

It is possible that in the future GNU C will support platforms where
`int` is 64 bits long. In practice, however, on today's real computers,
there is little variation; you can rely on the table given previously
(see [Basic Integers](Basic-Integers.md)).

To be completely sure of the size of an integer type, use the types
`int16_t`, `int32_t` and `int64_t`. Their corresponding unsigned types
add '`u`' at the front. To define these, include the header
file `stdint.h`.

The GNU C Compiler compiles for some embedded controllers that use two
bytes for `int`. On some, `int` is just one "byte," and so is
`short int`---but that "byte" may contain 16 bits or even 32 bits. These
processors can't support an ordinary operating system (they may have
their own specialized operating systems), and most C programs do not try
to support them.

------------------------------------------------------------------------

Previous: [Boolean Type](Boolean-Type.md), Up: [Integer Data
Types](Integer-Types.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
