Previous: [Aliasing and Length](Aliasing-Length.md), Up:
[Aliasing](Aliasing.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### B.3 Type Rules for Aliasing 

C code that converts a pointer to a different pointer type can use the
pointers to access the same memory locations with two different data
types. If the same address is accessed with different types in a single
control thread, optimization can make the code do surprising things (in
effect, make it malfunction).

Here's a concrete example where aliasing that can change the code's
behavior when it is optimized. We assume that `float` is 4 bytes long,
like `int`, and so is every pointer. Thus, the structures `struct a` and
`struct b` are both 8 bytes.

``` C
#include <stdio.h>
struct a { int size; char *data; };
struct b { float size; char *data; };

void sub (struct a *p, struct b *q)
{
  int x;
  p->size = 0;
  q->size = 1;
  x = p->size;
  printf("x       =%d\n", x);
  printf("p->size =%d\n", (int)p->size);
  printf("q->size =%d\n", (int)q->size);
}

int main(void)
{
  struct a foo;
  struct a *p = &foo;
  struct b *q = (struct b *) &foo;

  sub (p, q);
}
```

This code works as intended when compiled without optimization. All the
operations are carried out sequentially as written. The code sets `x` to
`p->size`, but what it actually gets is the bits of the floating point
number 1, as type `int`.

However, when optimizing, the compiler is allowed to assume (mistakenly,
here) that `q` does not point to the same storage as `p`, because their
data types are not allowed to alias.

From this assumption, the compiler can deduce (falsely, here) that the
assignment into `q->size` has no effect on the value of `p->size`, which
must therefore still be 0. Thus, `x` will be set to 0.

GNU C, following the C standard, *defines* this optimization as
legitimate. Code that misbehaves when optimized following these rules
is, by definition, incorrect C code.

The rules for storage aliasing in C are based on the two data types: the
type of the object, and the type it is accessed through. The rules
permit accessing part of a storage object of type `t` using
only these types:

-   `t`.
-   A type compatible with `t`. See [Compatible
    Types](Compatible-Types.md).
-   A signed or unsigned version of one of the above.
-   A qualifed version of one of the above. See [Type
    Qualifiers](Type-Qualifiers.md).
-   An array, structure (see [Structures](Structures.md)), or union
    type (`Unions`) that contains one of the above, either directly as a
    field or through multiple levels of fields. If `t` is
    `double`, this would include
    `struct s { union { double d[2]; int i[4]; } u; int i; };` because
    there's a `double` inside it somewhere.
-   A character type.

What do these rules say about the example in this subsection?

For `foo.size` (equivalently, `a->size`), `t` is `int`. The
type `float` is not allowed as an aliasing type by those rules, so
`b->size` is not supposed to alias with elements of `j`. Based on that
assumption, GNU C makes a permitted optimization that was not, in this
case, consistent with what the programmer intended the program to do.

Whether GCC actually performs type-based aliasing analysis depends on
the details of the code. GCC has other ways to determine (in some cases)
whether objects alias, and if it gets a reliable answer that way, it
won't fall back on type-based heuristics.

The importance of knowing the type-based aliasing rules is not so as to
ensure that the optimization is done where it would be safe, but so as
to ensure it is *not* done in a way that would break the program. You
can turn off type-based aliasing analysis by giving GCC the option
`-fno-strict-aliasing`.

------------------------------------------------------------------------

Previous: [Aliasing and Length](Aliasing-Length.md), Up:
[Aliasing](Aliasing.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
