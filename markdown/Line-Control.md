Next: [Null Directive](Null-Directive.md), Previous:
[Diagnostics](Diagnostics.md), Up: [Preprocessing](Preprocessing.md)
 
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 26.8 Line Control 


Due to C's widespread availability and low-level nature, it is often
used as the target language for translation of other languages, or for
the output of lexical analyzers and parsers (e.g., lex/flex and
yacc/bison). Line control enables the user to track diagnostics back to
the location in the original language.

The C compiler knows the location in the source file where each token
came from: file name, starting line and column, and final line and
column. (Column numbers are used only for error messages.)

When a program generates C source code, as the Bison parser generator
does, often it copies some of that C code from another file. For
instance parts of the output from Bison are generated from scratch or
come from a standard parser file, but Bison copies the rest from Bison's
input file. Errors in that code, at compile time or run time, should
refer to that file, which is the real source code. To make that happen,
Bison generates line-control directives that the C compiler understands.


`#line` is a directive that specifies the original line number and
source file name for subsequent code. `#line` has three variants:

`#line linenum`

-   `linenum`{.variable} is a non-negative decimal integer constant. It
    specifies the line number that should be reported for the following
    line of input. Subsequent lines are counted from
    `linenum`{.variable}.

`#line linenum filename`

-   `linenum`{.variable} is the same as for the first form, and has the
    same effect. In addition, `filename`{.variable} is a string constant
    that specifies the source file name. Subsequent source lines are
    recorded as coming from that file, until something else happens to
    change that. `filename`{.variable} is interpreted according to the
    normal rules for a string constant. Backslash escapes are
    interpreted, in contrast to `#include`.

`#line anything else`

-   `anything else`{.variable} is checked for macro calls, which are
    expanded. The result should match one of the above two forms.

`#line` directives alter the results of the `__FILE__` and `__LINE__`
symbols from that point on. See [Predefined
Macros](Predefined-Macros.md).

------------------------------------------------------------------------

Next: [Null Directive](Null-Directive.md), Previous:
[Diagnostics](Diagnostics.md), Up: [Preprocessing](Preprocessing.md)
 
[Contents](index.md#SEC_Contents "Table of contents")  
