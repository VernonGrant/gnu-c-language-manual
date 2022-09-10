Next: [The `#if` directive](if.md), Up: [Syntax of Preprocessing
Conditionals](Conditional-Syntax.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.6.2.1 The `#ifdef` directive 


The simplest sort of conditional is

``` C
#ifdef MACRO

controlled text

#endif /* MACRO */
```


This block is called a *conditional group*. The body,
`controlled text`{.variable}, will be included in compilation if and
only if `MACRO`{.variable} is defined. We say that the conditional
*succeeds* if `MACRO`{.variable} is defined, *fails* if it is not.

The `controlled text`{.variable} inside a conditional can include
preprocessing directives. They are executed only if the conditional
succeeds. You can nest conditional groups inside other conditional
groups, but they must be completely nested. In other words, `#endif`
always matches the nearest `#ifdef` (or `#ifndef`, or `#if`). Also, you
cannot start a conditional group in one file and end it in another.

Even if a conditional fails, the `controlled text`{.variable} inside it
is still run through initial transformations and tokenization.
Therefore, it must all be lexically valid C. Normally the only way this
matters is that all comments and string literals inside a failing
conditional group must still be properly ended.

The comment following the `#endif` is not required, but it is a good
practice if there is a lot of `controlled text`{.variable}, because it
helps people match the `#endif` to the corresponding `#ifdef`.

Older programs sometimes put `macro`{.variable} directly after the
`#endif` without enclosing it in a comment. This is invalid code
according to the C standard, but it only causes a warning in GNU C. It
never affects which `#ifndef` the `#endif` matches.


Sometimes you wish to use some code if a macro is *not* defined. You can
do this by writing `#ifndef` instead of `#ifdef`. One common use of
`#ifndef` is to include code only the first time a header file is
included. See [Once-Only Headers](Once_002dOnly-Headers.md).

Macro definitions can vary between compilations for several reasons.
Here are some samples.

-   Some macros are predefined on each kind of machine (see
    [System-specific Predefined
    Macros](https://gcc.gnu.org/onlinedocs/gcc/System_002dspecific-Predefined-Macros.md#System_002dspecific-Predefined-Macros)
    in Using the GNU Compiler Collection). This allows you to provide
    code specially tuned for a particular machine.
-   System header files define more macros, associated with the features
    they implement. You can test these macros with conditionals to avoid
    using a system feature on a machine where it is not implemented.
-   Macros can be defined or undefined with the `-D` and
    `-U` command-line options when you compile the program. You
    can arrange to compile the same source file into two different
    programs by choosing a macro name to specify which program you want,
    writing conditionals to test whether or how this macro is defined,
    and then controlling the state of the macro with command-line
    options, perhaps set in the file `Makefile`. See [Invoking
    GCC](https://gcc.gnu.org/onlinedocs/gcc/Invocation.md#Invocation)
    in Using the GNU Compiler Collection.
-   Your program might have a special header file (often called
    `config.h`) that is adjusted when the program is compiled.
    It can define or not define macros depending on the features of the
    system and the desired capabilities of the program. The adjustment
    can be automated by a tool such as `autoconf`, or done by hand.

------------------------------------------------------------------------

Next: [The `#if` directive](if.md), Up: [Syntax of Preprocessing
Conditionals](Conditional-Syntax.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
