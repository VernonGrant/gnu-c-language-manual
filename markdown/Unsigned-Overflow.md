Next: [Overflow with Signed Integers](Signed-Overflow.md), Up:
[Integer Overflow](Integer-Overflow.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 6.3.1 Overflow with Unsigned Integers 

Unsigned arithmetic in C ignores overflow; it produces the true result
modulo the `n`{.variable}th power of 2, where `n`{.variable} is the
number of bits in the data type. We say it "truncates" the true result
to the lowest `n`{.variable} bits.

A true result that is negative, when taken modulo the `n`{.variable}th
power of 2, yields a positive number. For instance,

``` C
unsigned int x = 1;
unsigned int y;

y = -x;
```

causes overflow because the negative number -1 can't be stored in an
unsigned type. The actual result, which is -1 modulo the
`n`{.variable}th power of 2, is one less than the `n`{.variable}th power
of 2. That is the largest value that the unsigned data type can store.
For a 32-bit `unsigned int`, the value is 4,294,967,295. See [Maximum
and Minimum Values](Maximum-and-Minimum-Values.md).

Adding that number to itself, as here,

``` C
unsigned int z;

z = y + y;
```

ought to yield 8,489,934,590; however, that is again too large to fit,
so overflow truncates the value to 4,294,967,294. If that were a signed
integer, it would mean -2, which (not by coincidence) equals -1 + -1.
