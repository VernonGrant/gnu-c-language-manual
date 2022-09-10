Next: [Error Recovery](Error-Recovery.md), Previous: [Significance
Loss](Significance-Loss.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 28.10 Fused Multiply-Add 


In 1990, when IBM introduced the POWER architecture, the CPU provided a
previously unknown instruction, the *fused multiply-add* (FMA). It
computes the value `x * y + z` with an **exact** double-length product,
followed by an addition with a *single* rounding. Numerical computation
often needs pairs of multiply and add operations, for which the FMA is
well-suited.

On the POWER architecture, there are two dedicated registers that hold
permanent values of `0.0` and `1.0`, and the normal *multiply* and *add*
instructions are just wrappers around the FMA that compute `x * y + 0.0`
and `x * 1.0 + z`, respectively.

In the early days, it appeared that the main benefit of the FMA was
getting two floating-point operations for the price of one, almost
doubling the performance of some algorithms. However, numerical analysts
have since shown numerous uses of the FMA for significantly enhancing
accuracy. We discuss one of the most important ones in the next section.

A few other architectures have since included the FMA, and most provide
variants for the related operations `x * y - z` (FMS), `-x * y + z`
(FNMA), and `-x * y - z` (FNMS).

The functions `fmaf`, `fma`, and `fmal` implement fused multiply-add for
the `float`, `double`, and `long double` data types. Correct
implementation of the FMA in software is difficult, and some systems
that appear to provide those functions do not satisfy the
single-rounding requirement. That situation should change as more
programmers use the FMA operation, and more CPUs provide FMA in
hardware.

Use the `-ffp-contract=fast` option to allow generation of FMA
instructions, or `-ffp-contract=off` to disallow it.

------------------------------------------------------------------------

Next: [Error Recovery](Error-Recovery.md), Previous: [Significance
Loss](Significance-Loss.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
