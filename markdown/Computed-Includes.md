Previous: [Once-Only Headers](Once_002dOnly-Headers.md), Up: [Header
Files](Header-Files.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.4.5 Computed Includes 


Sometimes it is necessary to select one of several different header
files to be included into your program. They might specify configuration
parameters to be used on different sorts of operating systems, for
instance. You could do this with a series of conditionals,

``` C
#if SYSTEM_1
# include "system_1.h"
#elif SYSTEM_2
# include "system_2.h"
#elif SYSTEM_3
/* … */
#endif
```

That rapidly becomes tedious. Instead, GNU C offers the ability to use a
macro for the header name. This is called a *computed include*. Instead
of writing a header name as the direct argument of `#include`, you
simply put a macro name there instead:

``` C
#define SYSTEM_H "system_1.h"
/* … */
#include SYSTEM_H
```

`SYSTEM_H` is expanded, then `system_1.h` is included as if the
`#include` had been written with that name. `SYSTEM_H` could be defined
by your Makefile with a `-D` option.

You must be careful when you define such a macro. `#define` saves
tokens, not text. GCC has no way of knowing that the macro will be used
as the argument of `#include`, so it generates ordinary tokens, not a
header name. This is unlikely to cause problems if you use double-quote
includes, which are syntactically similar to string constants. If you
use angle brackets, however, you may have trouble.

The syntax of a computed include is actually a bit more general than the
above. If the first non-whitespace character after `#include` is not
'`"`' or '`<`', then the entire line is macro-expanded
like running text would be.

If the line expands to a single string constant, the contents of that
string constant are the file to be included. Preprocessing does not
re-examine the string for embedded quotes, but neither does it process
backslash escapes in the string. Therefore

``` C
#define HEADER "a\"b"
#include HEADER
```

looks for a file named `a\"b`. Preprocessing searches for the
file according to the rules for double-quoted includes.

If the line expands to a token stream beginning with a '`<`'
token and including a '`>`' token, then the tokens between the
'`<`' and the first '`>`' are combined to form the
filename to be included. Any whitespace between tokens is reduced to a
single space; then any space after the initial '`<`' is
retained, but a trailing space before the closing '`>`' is
ignored. Preprocessing searches for the file according to the rules for
angle-bracket includes.

In either case, if there are any tokens on the line after the file name,
an error occurs and the directive is not processed. It is also an error
if the result of expansion does not match either of the two expected
forms.

These rules are implementation-defined behavior according to the C
standard. To minimize the risk of different compilers interpreting your
computed includes differently, we recommend you use only a single
object-like macro that expands to a string constant. That also makes it
clear to people reading your program.

------------------------------------------------------------------------

Previous: [Once-Only Headers](Once_002dOnly-Headers.md), Up: [Header
Files](Header-Files.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
