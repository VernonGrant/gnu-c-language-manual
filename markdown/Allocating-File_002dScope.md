Next: [`auto` and `register`](auto-and-register.md), Previous:
[`extern` Declarations](Extern-Declarations.md), Up:
[Variables](Variables.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 20.9 Allocating File-Scope Variables 


Some file-scope declarations allocate space for the variable, and some
don't.

A file-scope declaration with an initial value *must* allocate space for
the variable; if there are two of such declarations for the same
variable, even in different compilation modules, they conflict.

An `extern` declaration *never* allocates space for the variable. If all
the top-level declarations of a certain variable are `extern`, the
variable never gets memory space. If that variable is used anywhere in
the program, the use will be reported as an error, saying that the
variable is not defined.


A file-scope declaration without an initial value is called a *tentative
definition*. This is a strange hybrid: it *can* allocate space for the
variable, but does not insist. So it causes no conflict, no error, if
the variable has another declaration that allocates space for it,
perhaps in another compilation module. But if nothing else allocates
space for the variable, the tentative definition will do it. Any number
of compilation modules can declare the same variable in this way, and
that is sufficient for all of them to use the variable.

In programs that are very large or have many contributors, it may be
wise to adopt the convention of never using tentative definitions. You
can use the compilation option `-fno-common` to make them an
error, or `--warn-common` to warn about them.

If a file-scope variable gets its space through a tentative definition,
it starts out containing all zeros.
