Next: [Aliasing](Aliasing.md), Previous: [Directing
Compilation](Directing-Compilation.md), Up: [GNU C Manual](index.md)
 
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


## Appendix A Type Alignment 


Code for device drivers and other communication with low-level hardware
sometimes needs to be concerned with the alignment of data objects in
memory.

Each data type has a required *alignment*, always a power of 2, that
says at which memory addresses an object of that type can validly start.
A valid address for the type must be a multiple of its alignment. If a
type's alignment is 1, that means it can validly start at any address.
If a type's alignment is 2, that means it can only start at an even
address. If a type's alignment is 4, that means it can only start at an
address that is a multiple of 4.

The alignment of a type (except `char`) can vary depending on the kind
of computer in use. To refer to the alignment of a type in a C program,
use `_Alignof`, whose syntax parallels that of `sizeof`. Like `sizeof`,
`_Alignof` is a compile-time operation, and it doesn't compute the value
of the expression used as its argument.

Nominally, each integer and floating-point type has an alignment equal
to the largest power of 2 that divides its size. Thus, `int` with size 4
has a nominal alignment of 4, and `long long int` with size 8 has a
nominal alignment of 8.

However, each kind of computer generally has a maximum alignment, and no
type needs more alignment than that. If the computer's maximum alignment
is 4 (which is common), then no type's alignment is more than 4.

The size of any type is always a multiple of its alignment; that way, in
an array whose elements have that type, all the elements are properly
aligned if the first one is.

These rules apply to all real computers today, but some embedded
controllers have odd exceptions. We don't have references to cite for
them.

Ordinary C code guarantees that every object of a given type is in fact
aligned as that type requires.

If the operand of `_Alignof` is a structure field, the value is the
alignment it requires. It may have a greater alignment by coincidence,
due to the other fields, but `_Alignof` is not concerned about that. See
[Structures](Structures.md).

Older versions of GNU C used the keyword `__alignof__` for this, but now
that the feature has been standardized, it is better to use the standard
keyword `_Alignof`.


You can explicitly specify an alignment requirement for a particular
variable or structure field by adding `_Alignas (alignment)` to the
declaration, where `alignment`{.variable} is a power of 2 or a type
name. For instance:

``` C
char _Alignas (8) x;
```

or

``` C
char _Alignas (double) x;
```

specifies that `x` must start on an address that is a multiple of 8.
However, if `alignment`{.variable} exceeds the maximum alignment for the
machine, that maximum is how much alignment `x` will get.

The older GNU C syntax for this feature looked like
`__attribute__ ((__aligned__ (alignment)))` to the declaration, and was
added after the variable. For instance:

``` C
char x __attribute__ ((__aligned__ 8));
```

See [Attributes in Declarations](Attributes.md).

------------------------------------------------------------------------

Next: [Aliasing](Aliasing.md), Previous: [Directing
Compilation](Directing-Compilation.md), Up: [GNU C Manual](index.md)
 
[Contents](index.md#SEC_Contents "Table of contents")  
