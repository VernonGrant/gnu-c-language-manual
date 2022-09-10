Next: [Directives](Directives.md), Up:
[Preprocessing](Preprocessing.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 26.1 Preprocessing Overview 

GNU C performs preprocessing on each line of a C program as the first
stage of compilation. Preprocessing operates on a line only when it
contains a *preprocessing directive* or uses a *macro*---all other lines
pass through preprocessing unchanged.

Here are some jobs that preprocessing does. The rest of this chapter
gives the details.

-   Inclusion of header files. These are files (usually containing
    declarations and macro definitions) that can be substituted into
    your program.
-   Macro expansion. You can define *macros*, which are abbreviations
    for arbitrary fragments of C code. Preprocessing replaces the macros
    with their definitions. Some macros are automatically predefined.
-   Conditional compilation. You can include or exclude parts of the
    program according to various conditions.
-   Line control. If you use a program to combine or rearrange source
    files into an intermediate file that is then compiled, you can use
    line control to inform the compiler where each source line
    originally came from.
-   Compilation control. `#pragma` and `_Pragma` invoke some special
    compiler features in how to handle certain constructs.
-   Diagnostics. You can detect problems at compile time and issue
    errors or warnings.

Except for expansion of predefined macros, all these operations happen
only if you use preprocessing directives to request them.
