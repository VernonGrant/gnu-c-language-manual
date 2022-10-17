Next: [Structure Assignment](Structure-Assignment.md), Previous:
[Flexible Array Fields](Flexible-Array-Fields.md), Up:
[Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.12 Overlaying Different Structures 


Be careful about using different structure types to refer to the same
memory within one function, because GNU C can optimize code assuming it
never does that. See [Aliasing](Aliasing.md). Here's an example of the
kind of aliasing that can cause the problem:

``` C
struct a { int size; char *data; };
struct b { int size; char *data; };
struct a foo;
struct a *p = &foo;
struct b *q = (struct b *) &foo;
```

Here `q` points to the same memory that the variable `foo` occupies, but
they have two different types. The two types `struct a` and `struct b`
are defined alike, but they are not the same type. Interspersing
references using the two types, like this,

``` C
p->size = 0;
q->size = 1;
x = p->size;
```

allows GNU C to assume that `p->size` is still zero when it is copied
into `x`. The GNU C compiler "knows" that `q` points to a `struct b` and
this is not supposed to overlap with a `struct a`. Other compilers might
also do this optimization.

The ISO C standard considers such code erroneous, precisely so that this
optimization will not be incorrect.
