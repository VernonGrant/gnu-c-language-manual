Next: [Conditionals](Conditionals.md), Previous: [Header
Files](Header-Files.md), Up: [Preprocessing](Preprocessing.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 26.5 Macros 


A *macro* is a fragment of code that has been given a name. Whenever the
name is used, it is replaced by the contents of the macro. There are two
kinds of macros. They differ mostly in what they look like when they are
used. *Object-like* macros resemble data objects when used,
*function-like* macros resemble function calls.

You may define any valid identifier as a macro, even if it is a C
keyword. In the preprocessing stage, GCC does not know anything about
keywords. This can be useful if you wish to hide a keyword such as
`const` from an older compiler that does not understand it. However, the
preprocessing operator `defined` (see [The `defined`
test](defined.md)) can never be defined as a macro, and C`++`'s named
operators (see [C++ Named
Operators](https://gcc.gnu.org/onlinedocs/gcc/C_002b_002b-Named-Operators.md#C_002b_002b-Named-Operators)
in Using the GNU Compiler Collection) cannot be macros when compiling
C`++` code.

The operator `#` is used in macros for stringification of an argument
(see [Stringification](Stringification.md)), and `##` is used for
concatenation of arguments into larger tokens (see
[Concatenation](Concatenation.md))

-   [Object-like Macros](Object_002dlike-Macros.md)
-   [Function-like Macros](Function_002dlike-Macros.md)
-   [Macro Arguments](Macro-Arguments.md)
-   [Stringification](Stringification.md)
-   [Concatenation](Concatenation.md)
-   [Variadic Macros](Variadic-Macros.md)
-   [Predefined Macros](Predefined-Macros.md)
-   [Undefining and Redefining
    Macros](Undefining-and-Redefining-Macros.md)
-   [Directives Within Macro
    Arguments](Directives-Within-Macro-Arguments.md)
-   [Macro Pitfalls](Macro-Pitfalls.md)
