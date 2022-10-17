Next: [Maximum and Minimum Values](Maximum-and-Minimum-Values.md), Up:
[Integers in Depth](Integers-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 27.1 Integer Representations 


Modern computers store integer values as binary (base-2) numbers that
occupy a single unit of storage, typically either as an 8-bit `char`, a
16-bit `short int`, a 32-bit `int`, or possibly, a 64-bit
`long long int`. Whether a `long int` is a 32-bit or a 64-bit value is
system dependent.[^11^](#FOOT11)


The macro `CHAR_BIT`, defined in `limits.h`, gives the number
of bits in type `char`. On any real operating system, the value is 8.

The fixed sizes of numeric types necessarily limits their *range of
values*, and the particular encoding of integers decides what that range
is.


For unsigned integers, the entire space is used to represent a
nonnegative value. Signed integers are stored using *two's-complement
representation*: a signed integer with `n` bits has a range
from *-2^(`n`\ -\ 1)^* to -1 to 0 to 1 to
*+2^(`n`\ -\ 1)^ - 1*, inclusive. The leftmost, or
high-order, bit is called the *sign bit*.

In two's-complement representation, there is only one value that means
zero, and the most negative number lacks a positive counterpart. As a
result, negating that number causes overflow; in practice, its result is
that number back again. We will revisit that peculiarity shortly.

For example, a two's-complement signed 8-bit integer can represent all
decimal numbers from -128 to +127. Negating -128 ought to give +128, but
that value won't fit in 8 bits, so the operation yields -128.

Decades ago, there were computers that used other representations for
signed integers, but they are long gone and not worth any effort to
support. The GNU C language does not support them.

When an arithmetic operation produces a value that is too big to
represent, the operation is said to *overflow*. In C, integer overflow
does not interrupt the control flow or signal an error. What it does
depends on signedness.

For unsigned arithmetic, the result of an operation that overflows is
the `n` low-order bits of the correct value. If the correct
value is representable in `n` bits, that is always the
result; thus we often say that "integer arithmetic is exact," omitting
the crucial qualifying phrase "as long as the exact result is
representable."

In principle, a C program should be written so that overflow never
occurs for signed integers, but in GNU C you can specify various ways of
handling such overflow (see [Integer Overflow](Integer-Overflow.md)).

Integer representations are best understood by looking at a table for a
tiny integer size; here are the possible values for an integer with
three bits:

  Unsigned   Signed   Bits   2s Complement
  ---------- -------- ------ ---------------
  0          0        000    000 (0)
  1          1        001    111 (-1)
  2          2        010    110 (-2)
  3          3        011    101 (-3)
  4          -4       100    100 (-4)
  5          -3       101    011 (3)
  6          -2       110    010 (2)
  7          -1       111    001 (1)

The parenthesized decimal numbers in the last column represent the
signed meanings of the two's-complement of the line's value. Recall
that, in two's-complement encoding, the high-order bit is 0 when the
number is nonnegative.

We can now understand the peculiar behavior of negation of the most
negative two's-complement integer: start with 0b100, invert the bits to
get 0b011, and add 1: we get 0b100, the value we started with.

We can also see overflow behavior in two's-complement:

``` C
3 + 1 = 0b011 + 0b001 = 0b100 = (-4)
3 + 2 = 0b011 + 0b010 = 0b101 = (-3)
3 + 3 = 0b011 + 0b011 = 0b110 = (-2)
```

A sum of two nonnegative signed values that overflows has a 1 in the
sign bit, so the exact positive result is truncated to a negative value.


------------------------------------------------------------------------

#### Footnotes 

##### [(11)](#DOCF11)

In theory, any of these types could have some other size, bit it's not
worth even a minute to cater to that possibility. It never happens on
GNU/Linux.

------------------------------------------------------------------------

Next: [Maximum and Minimum Values](Maximum-and-Minimum-Values.md), Up:
[Integers in Depth](Integers-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
