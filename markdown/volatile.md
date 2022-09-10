Next: [`restrict`-Qualified Pointers](restrict-Pointers.md), Previous:
[`const` Variables and Fields](const.md), Up: [Type
Qualifiers](Type-Qualifiers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 21.2 `volatile` Variables and Fields 


The GNU C compiler often performs optimizations that eliminate the need
to write or read a variable. For instance,

``` C
int foo;
foo = 1;
foo++;
```

might simply store the value 2 into `foo`, without ever storing 1. These
optimizations can also apply to structure fields in some cases.

If the memory containing `foo` is shared with another program, or if it
is examined asynchronously by hardware, such optimizations could confuse
the communication. Using `volatile` is one way to prevent them.

Writing `volatile` with the type in a variable or field declaration says
that the value may be examined or changed for reasons outside the
control of the program at any moment. Therefore, the program must
execute in a careful way to assure correct interaction with those
accesses, whenever they may occur.

The simplest use looks like this:

``` C
volatile int lock;
```

This directs the compiler not to do certain common optimizations on use
of the variable `lock`. All the reads and writes for a volatile variable
or field are really done, and done in the order specified by the source
code. Thus, this code:

``` C
lock = 1;
list = list->next;
if (lock)
  lock_broken (&lock);
lock = 0;
```

really stores the value 1 in `lock`, even though there is no sign it is
really used, and the `if` statement reads and checks the value of
`lock`, rather than assuming it is still 1.

A limited amount of optimization can be done, in principle, on
`volatile` variables and fields: multiple references between two
sequence points (see [Sequence Points](Sequence-Points.md)) can be
simplified together.

Use of `volatile` does not eliminate the flexibility in ordering the
computation of the operands of most operators. For instance, in
`lock + foo ()`, the order of accessing `lock` and calling `foo` is not
specified, so they may be done in either order; the fact that `lock` is
`volatile` has no effect on that.

------------------------------------------------------------------------

Next: [`restrict`-Qualified Pointers](restrict-Pointers.md), Previous:
[`const` Variables and Fields](const.md), Up: [Type
Qualifiers](Type-Qualifiers.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
