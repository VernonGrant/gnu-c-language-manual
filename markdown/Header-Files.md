Next: [Macros](Macros.md), Previous: [Preprocessing
Tokens](Preprocessing-Tokens.md), Up:
[Preprocessing](Preprocessing.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 26.4 Header Files 


A header file is a file of C code, typically containing C declarations
and macro definitions (see [Macros](Macros.md)), to be shared between
several source files. You request the use of a header file in your
program by *including* it, with the C preprocessing directive
`#include`.

Header files serve two purposes.

-   [] System header files declare the
    interfaces to parts of the operating system. You include them in
    your program to supply the definitions and declarations that you
    need to invoke system calls and libraries.
-   Program-specific header files contain declarations for interfaces
    between the source files of a particular program. It is a good idea
    to create a header file for related declarations and macro
    definitions if all or most of them are needed in several different
    source files.

Including a header file produces the same results as copying the header
file into each source file that needs it. Such copying would be
time-consuming and error-prone. With a header file, the related
declarations appear in only one place. If they need to be changed, you
can change them in one place, and programs that include the header file
will then automatically use the new version when next recompiled. The
header file eliminates the labor of finding and changing all the copies
as well as the risk that a failure to change one copy will result in
inconsistencies within a program.

In C, the usual convention is to give header files names that end with
`.h`. It is most portable to use only letters, digits, dashes,
and underscores in header file names, and at most one dot.

The operation of including another source file isn't actually limited to
the sort of code we put into header files. You can put any sort of C
code into a separate file, then use `#include` to copy it virtually into
other C source files. But that is a strange thing to do.

-   [`#include` Syntax](include-Syntax.md)
-   [`#include` Operation](include-Operation.md)
-   [Search Path](Search-Path.md)
-   [Once-Only Headers](Once_002dOnly-Headers.md)
-   [Computed Includes](Computed-Includes.md)

------------------------------------------------------------------------

Next: [Macros](Macros.md), Previous: [Preprocessing
Tokens](Preprocessing-Tokens.md), Up:
[Preprocessing](Preprocessing.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
