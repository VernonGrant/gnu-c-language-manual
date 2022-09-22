Next: [`const` Fields](const-Fields.md), Previous: [Bit
Fields](Bit-Fields.md), Up: [Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 15.8 Bit Field Packing 

Programs to communicate with low-level hardware interfaces need to
define bit fields laid out to match the hardware data. This section
explains how to do that.

Consecutive bit fields are packed together, but each bit field must fit
within a single object of its specified type. In this example,

``` C
unsigned short a : 3, b : 3, c : 3, d : 3, e : 3;
```

all five fields fit consecutively into one two-byte `short`. They need
15 bits, and one `short` provides 16. By contrast,

``` C
unsigned char a : 3, b : 3, c : 3, d : 3, e : 3;
```

needs three bytes. It fits `a` and `b` into one `char`, but `c` won't
fit in that `char` (they would add up to 9 bits). So `c` and `d` go into
a second `char`, leaving a gap of two bits between `b` and `c`. Then `e`
needs a third `char`. By contrast,

``` C
unsigned char a : 3, b : 3;
unsigned int c : 3;
unsigned char d : 3, e : 3;
```

needs only two bytes: the type `unsigned int` allows `c` to straddle
bytes that are in the same word.

You can leave a gap of a specified number of bits by defining a nameless
bit field. This looks like `type : nbits;`. It is allocated space in the
structure just as a named bit field would be allocated.

You can force the following bit field to advance to the following
aligned memory object with `type : 0;`.

Both of these constructs can syntactically share `type` with
ordinary bit fields. This example illustrates both:

``` C
unsigned int a : 5, : 3, b : 5, : 0, c : 5, : 3, d : 5;
```

It puts `a` and `b` into one `int`, with a 3-bit gap between them. Then
`: 0` advances to the next `int`, so `c` and `d` fit into that one.

These rules for packing bit fields apply to most target platforms,
including all the usual real computers. A few embedded controllers have
special layout rules.

------------------------------------------------------------------------

Next: [`const` Fields](const-Fields.md), Previous: [Bit
Fields](Bit-Fields.md), Up: [Structures](Structures.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
