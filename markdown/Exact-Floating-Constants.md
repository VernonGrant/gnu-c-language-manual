Next: [Handling Infinity](Handling-Infinity.md), Previous: [Error
Recovery](Error-Recovery.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 28.12 Exact Floating-Point Constants 


One of the frustrations that numerical programmers have suffered with
since the dawn of digital computers is the inability to precisely
specify numbers in their programs. On the early decimal machines, that
was not an issue: you could write a constant `1e-30` and be confident of
that exact value being used in floating-point operations. However, when
the hardware works in a base other than 10, then human-specified numbers
have to be converted to that base, and then converted back again at
output time. The two base conversions are rarely exact, and unwanted
rounding errors are introduced.


As computers usually represent numbers in a base other than 10, numbers
often must be converted to and from different bases, and rounding errors
can occur during conversion. This problem is solved in C using
hexademical floating-point constants. For example, `+0x1.fffffcp-1` is
the number that is the IEEE 754 32-bit value closest to, but below,
`1.0`. The significand is represented as a hexadecimal fraction, and the
*power of two* is written in decimal following the exponent letter `p`
(the traditional exponent letter `e` is not possible, because it is a
hexadecimal digit).

In `printf` and `scanf` and related functions, you can use the
'`%a`' and '`%A`' format specifiers for writing and
reading hexadecimal floating-point values. '`%a`' writes them
with lower case letters and '`%A`' writes them with upper case
letters. For instance, this code reproduces our sample number:

``` C
printf ("%a\n", 1.0 - pow (2.0, -23));
    -| 0x1.fffffcp-1
```

The `strtod` family was similarly extended to recognize numbers in that
new format.

If you want to ensure exact data representation for transfer of
floating-point numbers between C programs on different computers, then
hexadecimal constants are an optimum choice.

------------------------------------------------------------------------

Next: [Handling Infinity](Handling-Infinity.md), Previous: [Error
Recovery](Error-Recovery.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
