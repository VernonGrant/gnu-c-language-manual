Previous: [Overflow with Unsigned Integers](Unsigned-Overflow.md), Up:
[Integer Overflow](Integer-Overflow.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 6.3.2 Overflow with Signed Integers 


For signed integers, the result of overflow in C is *in principle*
undefined, meaning that anything whatsoever could happen. Therefore, C
compilers can do optimizations that treat the overflow case with total
unconcern. (Since the result of overflow is undefined in principle, one
cannot claim that these optimizations are erroneous.)

**Watch out:** These optimizations can do surprising things. For
instance,

``` C
int i;
…
if (i < i + 1)
  x = 5;
```

could be optimized to do the assignment unconditionally, because the
`if`-condition is always true if `i + 1` does not overflow.

GCC offers compiler options to control handling signed integer overflow.
These options operate per module; that is, each module behaves according
to the options it was compiled with.

These two options specify particular ways to handle signed integer
overflow, other than the default way:

`-fwrapv`

-   Make signed integer operations well-defined, like unsigned integer
    operations: they produce the `n` low-order bits of the
    true result. The highest of those `n` bits is the sign
    bit of the result. With `-fwrapv`, these out-of-range
    operations are not considered overflow, so (strictly speaking)
    integer overflow never happens.

    The option `-fwrapv` enables some optimizations based on
    the defined values of out-of-range results. In GCC 8, it disables
    optimizations that are based on assuming signed integer operations
    will not overflow.

`-ftrapv`

-   Generate a signal `SIGFPE` when signed integer overflow occurs. This
    terminates the program unless the program handles the signal. See
    [Signals](Signals.md).

One other option is useful for finding where overflow occurs:

`-fsanitize=signed-integer-overflow`

-   Output a warning message at run time when signed integer overflow
    occurs. This checks the '`+`', '`*`', and
    '`-`' operators. This takes priority over
    `-ftrapv`.

------------------------------------------------------------------------

Previous: [Overflow with Unsigned Integers](Unsigned-Overflow.md), Up:
[Integer Overflow](Integer-Overflow.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
