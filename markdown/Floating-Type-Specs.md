Next: [Special Floating-Point Values](Special-Float-Values.md),
Previous: [Floating-Point
Representations](Floating-Representations.md), Up: [Floating Point in
Depth](Floating-Point-in-Depth.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 28.2 Floating-Point Type Specifications 

The standard library header file `float.h` defines a number of
constants that describe the platform's implementation of floating-point
types `float`, `double` and `long double`. They include:


`FLT_MIN`\
`DBL_MIN`\
`LDBL_MIN`

-   Defines the minimum normalized positive floating-point values that
    can be represented with the type.

`FLT_HAS_SUBNORM`\
`DBL_HAS_SUBNORM`\
`LDBL_HAS_SUBNORM`

-   Defines if the floating-point type supports subnormal (or
    "denormalized") numbers or not (see [subnormal
    numbers](Special-Float-Values.md#subnormal-numbers)).

`FLT_TRUE_MIN`\
`DBL_TRUE_MIN`\
`LDBL_TRUE_MIN`

-   Defines the minimum positive values (including subnormal values)
    that can be represented with the type.

`FLT_MAX`\
`DBL_MAX`\
`LDBL_MAX`

-   Defines the largest values that can be represented with the type.

`FLT_DECIMAL_DIG`\
`DBL_DECIMAL_DIG`\
`LDBL_DECIMAL_DIG`

-   Defines the number of decimal digits `n` such that any
    floating-point number that can be represented in the type can be
    rounded to a floating-point number with `n` decimal digits, and back
    again, without losing any precision of the value.
