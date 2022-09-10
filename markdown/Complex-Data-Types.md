Next: [The Void Type](The-Void-Type.md), Previous: [Floating-Point
Data Types](Floating_002dPoint-Data-Types.md), Up: [Primitive Data
Types](Primitive-Types.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 11.3 Complex Data Types 


Complex numbers can include both a real part and an imaginary part. The
numeric constants covered above have real-numbered values. An
imaginary-valued constant is an ordinary real-valued constant followed
by '`i`'.

To declare numeric variables as complex, use the `_Complex`
keyword.[^4^](#FOOT4) The standard C complex data types are
floating point,

``` C
_Complex float foo;
_Complex double bar;
_Complex long double quux;
```

but GNU C supports integer complex types as well.

Since `_Complex` is a keyword just like `float` and `double` and `long`,
the keywords can appear in any order, but the order shown above seems
most logical.

GNU C supports constants for complex values; for instance, `4.0 + 3.0i`
has the value 4 + 3i as type `_Complex double`. See [Imaginary
Constants](Imaginary-Constants.md).

To pull the real and imaginary parts of the number back out, GNU C
provides the keywords `__real__` and `__imag__`:

``` C
_Complex double foo = 4.0 + 3.0i;

double a = __real__ foo; /* a is now 4.0. */
double b = __imag__ foo; /* b is now 3.0. */
```

Standard C does not include these keywords, and instead relies on
functions defined in `complex.h` for accessing the real and imaginary
parts of a complex number: `crealf`, `creal`, and `creall` extract the
real part of a float, double, or long double complex number,
respectively; `cimagf`, `cimag`, and `cimagl` extract the imaginary
part.


GNU C also defines '`~`' as an operator for complex
conjugation, which means negating the imaginary part of a complex
number:

``` C
_Complex double foo = 4.0 + 3.0i;
_Complex double bar = ~foo; /* bar is now 4 - 3i. */
```

For standard C compatibility, you can use the appropriate library
function: `conjf`, `conj`, or `confl`.


------------------------------------------------------------------------

#### Footnotes 

##### [(4)](#DOCF4)

For compatibility with older versions of GNU C, the keyword
`__complex__` is also allowed. Going forward, however, use the new
`_Complex` keyword as defined in ISO C11.

------------------------------------------------------------------------

Next: [The Void Type](The-Void-Type.md), Previous: [Floating-Point
Data Types](Floating_002dPoint-Data-Types.md), Up: [Primitive Data
Types](Primitive-Types.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
