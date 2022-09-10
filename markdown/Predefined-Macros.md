Next: [Undefining and Redefining
Macros](Undefining-and-Redefining-Macros.md), Previous: [Variadic
Macros](Variadic-Macros.md), Up: [Macros](Macros.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.5.7 Predefined Macros 


Several object-like macros are predefined; you use them without
supplying their definitions. Here we explain the ones user programs
often need to use. Many other macro names starting with '`__`'
are predefined; in general, you should not define such macro names
yourself.

`__FILE__`

-   This macro expands to the name of the current input file, in the
    form of a C string constant. This is the full name by which the GCC
    opened the file, not the short name specified in `#include` or as
    the input file name argument. For example,
    `"/usr/local/include/myheader.h"` is a possible expansion of this
    macro.

`__LINE__`

-   This macro expands to the current input line number, in the form of
    a decimal integer constant. While we call it a predefined macro,
    it's a pretty strange macro, since its "definition" changes with
    each new line of source code.

`__func__`\
`__FUNCTION__`

-   These names are like variables that have as value a string
    containing the name of the current function definition. They are not
    really macros, but this is the best place to mention them.

    `__FUNCTION__` is the name that has been defined in GNU C since time
    immemorial; `__func__` is defined by the C standard. With the
    following conditionals, you can use whichever one is defined.

    
    ``` C
    #if __STDC_VERSION__ < 199901L
    # if __GNUC__ >= 2
    #  define __func__ __FUNCTION__
    # else
    #  define __func__ "<unknown>"
    # endif
    #endif
    ```
    

`__PRETTY_FUNCTION__`

-   This is equivalent to `__FUNCTION__` in C, but in C`++` the string
    includes argument type information as well. It is a GNU C extension.

Those features are useful in generating an error message to report an
inconsistency detected by the program; the message can state the source
line where the inconsistency was detected. For example,

``` C
fprintf (stderr, "Internal error: "
                 "negative string length "
                 "in function %s "
                 "%d at %s, line %d.",
         __func__, length, __FILE__, __LINE__);
```

A `#line` directive changes `__LINE__`, and may change `__FILE__` as
well. See [Line Control](Line-Control.md).

`__DATE__`

-   This macro expands to a string constant that describes the date of
    compilation. The string constant contains eleven characters and
    looks like `"Feb 12 1996"`. If the day of the month is just one
    digit, an extra space precedes it so that the date is always eleven
    characters.

    If the compiler cannot determine the current date, it emits a
    warning messages (once per compilation) and `__DATE__` expands to
    `"??? ?? ????"`.

    We deprecate the use of `__DATE__` for the sake of reproducible
    compilation.

`__TIME__`

-   This macro expands to a string constant that describes the time of
    compilation. The string constant contains eight characters and looks
    like `"23:59:01"`.

    If the compiler cannot determine the current time, it emits a
    warning message (once per compilation) and `__TIME__` expands to
    `"??:??:??"`.

    We deprecate the use of `__TIME__` for the sake of reproducible
    compilation.

`__STDC__`

-   In normal operation, this macro expands to the constant 1, to
    signify that this compiler implements ISO Standard C.

`__STDC_VERSION__`

-   This macro expands to the C Standard's version number, a long
    integer constant of the form `yyyymmL` where `yyyy` and
    `mm` are the year and month of the Standard version. This
    states which version of the C Standard the compiler implements.

    The current default value is `201112L`, which signifies the C 2011
    standard.

`__STDC_HOSTED__`

-   This macro is defined, with value 1, if the compiler's target is a
    *hosted environment*. A hosted environment provides the full
    facilities of the standard C library.

The rest of the predefined macros are GNU C extensions.

`__COUNTER__`

-   This macro expands to sequential integral values starting from 0. In
    other words, each time the program uses this acro, it generates the
    next successive integer. This, with the `##` operator, provides a
    convenient means for macros to generate unique identifiers.

`__GNUC__`\
`__GNUC_MINOR__`\
`__GNUC_PATCHLEVEL__`

-   These macros expand to the major version, minor version, and patch
    level of the compiler, as integer constants. For example, GCC 3.2.1
    expands `__GNUC__` to 3, `__GNUC_MINOR__` to 2, and
    `__GNUC_PATCHLEVEL__` to 1.

    If all you need to know is whether or not your program is being
    compiled by GCC, or a non-GCC compiler that claims to accept the GNU
    C extensions, you can simply test `__GNUC__`. If you need to write
    code that depends on a specific version, you must check more
    carefully. Each change in the minor version resets the patch level
    to zero; each change in the major version (which happens rarely)
    resets the minor version and the patch level to zero. To use the
    predefined macros directly in the conditional, write it like this:

    
    ``` C
    /* Test for version 3.2.0 or later. */
    #if __GNUC__ > 3 || \
        (__GNUC__ == 3 && (__GNUC_MINOR__ > 2 || \
                           (__GNUC_MINOR__ == 2 && \
                            __GNUC_PATCHLEVEL__ > 0))
    ```
    

    Another approach is to use the predefined macros to calculate a
    single number, then compare that against a threshold:

    
    ``` C
    #define GCC_VERSION (__GNUC__ * 10000 \
                         + __GNUC_MINOR__ * 100 \
                         + __GNUC_PATCHLEVEL__)
    /* … */
    /* Test for GCC > 3.2.0 */
    #if GCC_VERSION > 30200
    ```
    

    Many people find this form easier to understand.

`__VERSION__`

-   This macro expands to a string constant that describes the version
    of the compiler in use. You should not rely on its contents' having
    any particular form, but you can count on it to contain at least the
    release number.

`__TIMESTAMP__`

-   This macro expands to a string constant that describes the date and
    time of the last modification of the current source file. The string
    constant contains abbreviated day of the week, month, day of the
    month, time in hh:mm:ss form, and the year, in the format
    `"Sun Sep 16 01:03:52 1973"`. If the day of the month is less than
    10, it is padded with a space on the left.

    If GCC cannot determine that information date, it emits a warning
    message (once per compilation) and `__TIMESTAMP__` expands to
    `"??? ??? ?? ??:??:?? ????"`.

    We deprecate the use of this macro for the sake of reproducible
    compilation.

------------------------------------------------------------------------

Next: [Undefining and Redefining
Macros](Undefining-and-Redefining-Macros.md), Previous: [Variadic
Macros](Variadic-Macros.md), Up: [Macros](Macros.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
