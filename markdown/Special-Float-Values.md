Next: [Invalid Optimizations](Invalid-Optimizations.md), Previous:
[Floating-Point Type Specifications](Floating-Type-Specs.md), Up:
[Floating Point in Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 28.3 Special Floating-Point Values 


IEEE floating point provides for special values that are not ordinary
numbers.

infinities

-   `+Infinity` and `-Infinity` are two different infinite values, one
    positive and one negative. These result from operations such as
    `1 / 0`, `Infinity + Infinity`, `Infinity * Infinity`, and
    `Infinity + finite`, and also from a result that is finite, but
    larger than the most positive possible value or smaller than the
    most negative possible value.

    See [Handling Infinity](Handling-Infinity.md), for more about
    working with infinities.

NaNs (not a number) [¶](#index-QNaN){.copiable-anchor}

-   []

    There are two special values, called Not-a-Number (NaN): a quiet NaN
    (QNaN), and a signaling NaN (SNaN).

    A QNaN is produced by operations for which the value is undefined in
    real arithmetic, such as `0 / 0`, `sqrt (-1)`,
    `Infinity - Infinity`, and any basic operation in which an operand
    is a QNaN.

    The signaling NaN is intended for initializing otherwise-unassigned
    storage, and the goal is that unlike a QNaN, an SNaN *does* cause an
    interrupt that can be caught by a software handler, diagnosed, and
    reported. In practice, little use has been made of signaling NaNs,
    because the most common CPUs in desktop and portable computers fail
    to implement the full IEEE 754 Standard, and supply only one kind of
    NaN, the quiet one. Also, programming-language standards have taken
    decades to catch up to the IEEE 754 standard, and implementations of
    those language standards make an additional delay before programmers
    become willing to use these features.

    To enable support for signaling NaNs, use the GCC command-line
    option `-fsignaling-nans`, but this is an experimental
    feature and may not work as expected in every situation.

    A NaN has a sign bit, but its value means nothing.

    See [Handling NaN](Handling-NaN.md), for more about working with
    NaNs.

subnormal numbers [¶](#index-subnormal-numbers){.copiable-anchor}

-   []
    []

    It can happen that a computed floating-point value is too small to
    represent, such as when two tiny numbers are multiplied. The result
    is then said to *underflow*. The traditional behavior before the
    IEEE 754 Standard was to use zero as the result, and possibly to
    report the underflow in some sort of program output.

    The IEEE 754 Standard is vague about whether rounding happens before
    detection of floating underflow and overflow, or after, and CPU
    designers may choose either.

    However, the Standard does something unusual compared to earlier
    designs, and that is that when the result is smaller than the
    smallest *normalized* representable value (i.e., one in which the
    leading significand bit is `1`), the normalization requirement is
    relaxed, leading zero bits are permitted, and precision is gradually
    lost until there are no more bits in the significand. That
    phenomenon is called *gradual underflow*, and it serves important
    numerical purposes, although it does reduce the precision of the
    final result. Some floating-point designs allow you to choose at
    compile time, or even at run time, whether underflows are gradual,
    or are flushed abruptly to zero. Numbers that have entered the
    region of gradual underflow are called *subnormal*.

    You can use the library functions `fesetround` and `fegetround` to
    set and get the rounding mode. Rounding modes are defined (if
    supported by the platform) in `fenv.h` as: `FE_UPWARD` to round
    toward positive infinity; `FE_DOWNWARD` to round toward negative
    infinity; `FE_TOWARDZERO` to round toward zero; and `FE_TONEAREST`
    to round to the nearest representable value, the default mode. It is
    best to use `FE_TONEAREST` except when there is a special need for
    some other mode.

------------------------------------------------------------------------

Next: [Invalid Optimizations](Invalid-Optimizations.md), Previous:
[Floating-Point Type Specifications](Floating-Type-Specs.md), Up:
[Floating Point in Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
