Next: [Bit Fields](Bit-Fields.md), Previous: [Structure
Layout](Structure-Layout.md), Up: [Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.6 Packed Structures 


In GNU C you can force a structure to be laid out with no gaps by adding
`__attribute__((packed))` after `struct` (or at the end of the structure
type declaration). Here's an example:

``` C
struct __attribute__((packed)) foo
{
  char a;
  int c;
  char b;
};
```

Without `__attribute__((packed))`, this structure occupies 12 bytes (as
described in the previous section), assuming 4-byte alignment for `int`.
With `__attribute__((packed))`, it is only 6 bytes long---the sum of the
lengths of its fields.

Use of `__attribute__((packed))` often results in fields that don't have
the normal alignment for their types. Taking the address of such a field
can result in an invalid pointer because of its improper alignment.
Dereferencing such a pointer can cause a `SIGSEGV` signal on a machine
that doesn't, in general, allow unaligned pointers.

See [Attributes in Declarations](Attributes.md).
