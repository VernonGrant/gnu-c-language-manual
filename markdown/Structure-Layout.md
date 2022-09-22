Next: [Packed Structures](Packed-Structures.md), Previous: [Field
Offset](Field-Offset.md), Up: [Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.5 Structure Layout 


The rest of this chapter covers advanced topics about structures. If you
are just learning C, you can skip it.

The precise layout of a `struct` type is crucial when using it to
overlay hardware registers, to access data structures in shared memory,
or to assemble and disassemble packets for network communication. It is
also important for avoiding memory waste when the program makes many
objects of that type. However, the layout depends on the target
platform. Each platform has conventions for structure layout, which
compilers need to follow.

Here are the conventions used on most platforms.

The structure's fields appear in the structure layout in the order they
are declared. When possible, consecutive fields occupy consecutive bytes
within the structure. However, if a field's type demands more alignment
than it would get that way, C gives it the alignment it requires by
leaving a gap after the previous field.

Once all the fields have been laid out, it is possible to determine the
structure's alignment and size. The structure's alignment is the maximum
alignment of any of the fields in it. Then the structure's size is
rounded up to a multiple of its alignment. That may require leaving a
gap at the end of the structure.

Here are some examples, where we assume that `char` has size and
alignment 1 (always true), and `int` has size and alignment 4 (true on
most kinds of computers):

``` C
struct foo
{
  char a, b;
  int c;
};
```

This structure occupies 8 bytes, with an alignment of 4. `a` is at
offset 0, `b` is at offset 1, and `c` is at offset 4. There is a gap of
2 bytes before `c`.

Contrast that with this structure:

``` C
struct foo
{
  char a;
  int c;
  char b;
};
```

This structure has size 12 and alignment 4. `a` is at offset 0, `c` is
at offset 4, and `b` is at offset 8. There are two gaps: three bytes
before `c`, and three bytes at the end.

These two structures have the same contents at the C level, but one
takes 8 bytes and the other takes 12 bytes due to the ordering of the
fields. A reliable way to avoid this sort of wastage is to order the
fields by size, biggest fields first.

------------------------------------------------------------------------

Next: [Packed Structures](Packed-Structures.md), Previous: [Field
Offset](Field-Offset.md), Up: [Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
