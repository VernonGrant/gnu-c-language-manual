Next: [Old-Style Function
Definitions](Old_002dStyle-Function-Definitions.md), Up: [Obsolete
Function Features](Obsolete-Definitions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 22.8.1 Older GNU C Inlining 

The GNU C spec for inline functions, before GCC version 5, defined
`extern inline` on a function definition to mean to inline calls to it
but *not* generate code for the function that could be called at run
time. By contrast, `inline` without `extern` specified to generate
run-time code for the function. In effect, ISO incompatibly flipped the
meanings of these two cases. We changed GCC in version 5 to adopt the
ISO specification.

Many programs still use these cases with the previous GNU C meanings.
You can specify use of those meanings with the option
`-fgnu89-inline`. You can also specify this for a single
function with `__attribute__ ((gnu_inline))`. Here's an example:

``` C
inline __attribute__ ((gnu_inline))
int
inc (int *a)
{
  (*a)++;
}
```
