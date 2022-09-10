Next: [Diagnostics](Diagnostics.md), Previous: [Macros](Macros.md),
Up: [Preprocessing](Preprocessing.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 26.6 Conditionals 


A *conditional* is a preprocessing directive that controls whether or
not to include a chunk of code in the final token stream that is
compiled. Preprocessing conditionals can test arithmetic expressions, or
whether a name is defined as a macro, or both together using the special
`defined` operator.

A preprocessing conditional in C resembles in some ways an `if`
statement in C, but it is important to understand the difference between
them. The condition in an `if` statement is tested during the execution
of your program. Its purpose is to allow your program to behave
differently from run to run, depending on the data it is operating on.
The condition in a preprocessing conditional directive is tested when
your program is compiled. Its purpose is to allow different code to be
included in the program depending on the situation at the time of
compilation.

Sometimes this distinction makes no practical difference. GCC and other
modern compilers often do test `if` statements when a program is
compiled, if their conditions are known not to vary at run time, and
eliminate code that can never be executed. If you can count on your
compiler to do this, you may find that your program is more readable if
you use `if` statements with constant conditions (perhaps determined by
macros). Of course, you can only use this to exclude code, not type
definitions or other preprocessing directives, and you can only do it if
the file remains syntactically valid when that code is not used.

-   [Uses of Conditional Directives](Conditional-Uses.md)
-   [Syntax of Preprocessing Conditionals](Conditional-Syntax.md)
-   [Deleted Code](Deleted-Code.md)

------------------------------------------------------------------------

Next: [Diagnostics](Diagnostics.md), Previous: [Macros](Macros.md),
Up: [Preprocessing](Preprocessing.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
