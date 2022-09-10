Next: [Computed Includes](Computed-Includes.md), Previous: [Search
Path](Search-Path.md), Up: [Header Files](Header-Files.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.4.4 Once-Only Headers 


If a header file happens to be included twice, the compiler will process
its contents twice. This is very likely to cause an error, e.g. when the
compiler sees the same structure definition twice.

The standard way to prevent this is to enclose the entire real contents
of the file in a conditional, like this:

``` C
/* File foo.  */
#ifndef FILE_FOO_SEEN
#define FILE_FOO_SEEN

the entire file

#endif /* !FILE_FOO_SEEN */
```

This construct is commonly known as a *wrapper #ifndef*. When the header
is included again, the conditional will be false, because
`FILE_FOO_SEEN` is defined. Preprocessing skips over the entire contents
of the file, so that compilation will never "see" the file contents
twice in one module.

GCC optimizes this case even further. It remembers when a header file
has a wrapper `#ifndef`. If a subsequent `#include` specifies that
header, and the macro in the `#ifndef` is still defined, it does not
bother to rescan the file at all.

You can put comments in the header file outside the wrapper. They do not
interfere with this optimization.


The macro `FILE_FOO_SEEN` is called the *controlling macro* or *guard
macro*. In a user header file, the macro name should not begin with
'`_`'. In a system header file, it should begin with
'`__`' (or '`_`' followed by an upper-case letter) to
avoid conflicts with user programs. In any kind of header file, the
macro name should contain the name of the file and some additional text,
to avoid conflicts with other header files.

------------------------------------------------------------------------

Next: [Computed Includes](Computed-Includes.md), Previous: [Search
Path](Search-Path.md), Up: [Header Files](Header-Files.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
