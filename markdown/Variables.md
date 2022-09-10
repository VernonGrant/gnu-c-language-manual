Next: [Type Qualifiers](Type-Qualifiers.md), Previous:
[Statements](Statements.md), Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


## 20 Variables 


Every variable used in a C program needs to be made known by a
*declaration*. It can be used only after it has been declared. It is an
error to declare a variable name more than once in the same scope; an
exception is that `extern` declarations and tentative definitions can
coexist with another declaration of the same variable.

Variables can be declared anywhere within a block or file. (Older
versions of C required that all variable declarations within a block
occur before any statements.)

Variables declared within a function or block are *local* to it. This
means that the variable name is visible only until the end of that
function or block, and the memory space is allocated only while control
is within it.

Variables declared at the top level in a file are called *file-scope*.
They are assigned fixed, distinct memory locations, so they retain their
values for the whole execution of the program.

-   [Variable Declarations](Variable-Declarations.md)
-   [Initializers](Initializers.md)
-   [Designated Initializers](Designated-Inits.md)
-   [Referring to a Type with `__auto_type`](Auto-Type.md)
-   [Local Variables](Local-Variables.md)
-   [File-Scope Variables](File_002dScope-Variables.md)
-   [Static Local Variables](Static-Local-Variables.md)
-   [`extern` Declarations](Extern-Declarations.md)
-   [Allocating File-Scope Variables](Allocating-File_002dScope.md)
-   [`auto` and `register`](auto-and-register.md)
-   [Omitting Types in Declarations](Omitting-Types.md)
