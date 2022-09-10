Next: [`#include` Operation](include-Operation.md), Up: [Header
Files](Header-Files.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.4.1 `#include` Syntax 


You can specify inclusion of user and system header files with the
preprocessing directive `#include`. It has two variants:

`#include <file>`

-   This variant is used for system header files. It searches for a file
    named `file`{.variable} in a standard list of system directories.
    You can prepend directories to this list with the `-I`
    option (see [Invoking
    GCC](https://gcc.gnu.org/onlinedocs/gcc/Invocation.md#Invocation)
    in Using the GNU Compiler Collection).

`#include "file"`

-   This variant is used for header files of your own program. It
    searches for a file named `file`{.variable} first in the directory
    containing the current file, then in the quote directories, then the
    same directories used for `<file>`. You can prepend directories to
    the list of quote directories with the `-iquote` option.

The argument of `#include`, whether delimited with quote marks or angle
brackets, behaves like a string constant in that comments are not
recognized, and macro names are not expanded. Thus, `#include <x/*y>`
specifies inclusion of a system header file named `x/*y`.

However, if backslashes occur within `file`{.variable}, they are
considered ordinary text characters, not escape characters: character
escape sequences such as used in string constants in C are not
meaningful here. Thus, `#include "x\n\\y"` specifies a filename
containing three backslashes. By the same token, there is no way to
escape '`"`' or '`>`' to include it in the header file
name if it would instead end the file name.

Some systems interpret '`\`' as a file name component
separator. All these systems also interpret '`/`' the same way.
It is most portable to use only '`/`'.

It is an error to put anything other than comments on the `#include`
line after the file name.

------------------------------------------------------------------------

Next: [`#include` Operation](include-Operation.md), Up: [Header
Files](Header-Files.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
