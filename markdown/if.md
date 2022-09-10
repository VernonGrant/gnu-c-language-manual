Next: [The `defined` test](defined.md), Previous: [The `#ifdef`
directive](ifdef.md), Up: [Syntax of Preprocessing
Conditionals](Conditional-Syntax.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.6.2.2 The `#if` directive 

The `#if` directive allows you to test the value of an integer
arithmetic expression, rather than the mere existence of one macro. Its
syntax is

``` C
#if expression

controlled text

#endif /* expression */
```

`expression` is a C expression of integer type, subject to
stringent restrictions so its value can be computed at compile time. It
may contain

-   Integer constants.

-   Character constants, which are interpreted as they would be in
    normal code.

-   Arithmetic operators for addition, subtraction, multiplication,
    division, bitwise operations, shifts, comparisons, and logical
    operations (`&&` and `||`). The latter two obey the usual
    short-circuiting rules of standard C.

-   Macros. All macros in the expression are expanded before actual
    computation of the expression's value begins.

-   Uses of the `defined` operator, which lets you check whether macros
    are defined in the middle of an `#if`.

-   Identifiers that are not macros, which are all considered to be the
    number zero. This allows you to write `#if MACRO` instead of
    `#ifdef MACRO`, if you know that MACRO, when defined, will always
    have a nonzero value. Function-like macros used without their
    function call parentheses are also treated as zero.

    In some contexts this shortcut is undesirable. The
    `-Wundef` requests warnings for any identifier in an `#if`
    that is not defined as a macro.

Preprocessing does not know anything about the data types of C.
Therefore, `sizeof` operators are not recognized in `#if`; `sizeof` is
simply an identifier, and if it is not a macro, it stands for zero. This
is likely to make the expression invalid. Preprocessing does not
recognize `enum` constants; they too are simply identifiers, so if they
are not macros, they stand for zero.

Preprocessing calculates the value of `expression`, and
carries out all calculations in the widest integer type known to the
compiler; on most machines supported by GNU C this is 64 bits. This is
not the same rule as the compiler uses to calculate the value of a
constant expression, and may give different results in some cases. If
the value comes out to be nonzero, the `#if` succeeds and the
`controlled text` is compiled; otherwise it is skipped.

------------------------------------------------------------------------

Next: [The `defined` test](defined.md), Previous: [The `#ifdef`
directive](ifdef.md), Up: [Syntax of Preprocessing
Conditionals](Conditional-Syntax.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
