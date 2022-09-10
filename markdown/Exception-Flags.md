Next: [Exact Floating-Point Arithmetic](Exact-Floating_002dPoint.md),
Previous: [Invalid Optimizations](Invalid-Optimizations.md), Up:
[Floating Point in Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 28.5 Floating Arithmetic Exception Flags 


*Sticky exception flags* record the occurrence of particular conditions:
once set, they remain set until the program explicitly clears them.

The conditions include *invalid operand*, *division-by_zero*, *inexact
result* (i.e., one that required rounding), *underflow*, and *overflow*.
Some extended floating-point designs offer several additional exception
flags. The functions `feclearexcept`, `feraiseexcept`, `fetestexcept`,
`fegetexceptflags`, and `fesetexceptflags` provide a standardized
interface to those flags. See [Status bit
operations](https://www.gnu.org/software/libc/manual/html_node/Status-bit-operations.md#Status-bit-operations)
in The GNU C Library Reference Manual.

One important use of those []flags is to do a computation
that is normally expected to be exact in floating-point arithmetic, but
occasionally might not be, in which case, corrective action is needed.
You can clear the *inexact result* flag with a call to
`feclearexcept (FE_INEXACT)`, do the computation, and then test the flag
with `fetestexcept (FE_INEXACT)`; the result of that call is 0 if the
flag is not set (there was no rounding), and 1 when there was rounding
(which, we presume, implies the program has to correct for that).
