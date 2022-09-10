Previous: [Self-Referential Macros](Self_002dReferential-Macros.md),
Up: [Macro Pitfalls](Macro-Pitfalls.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.5.10.7 Argument Prescan 


Macro arguments are completely macro-expanded before they are
substituted into a macro body, unless they are stringified or pasted
with other tokens. After substitution, the entire macro body, including
the substituted arguments, is scanned again for macros to be expanded.
The result is that the arguments are scanned *twice* to expand macro
calls in them.

Most of the time, this has no effect. If the argument contained any
macro calls, they were expanded during the first scan. The result
therefore contains no macro calls, so the second scan does not change
it. If the argument were substituted as given, with no prescan, the
single remaining scan would find the same macro calls and produce the
same results.

You might expect the double scan to change the results when a
self-referential macro is used in an argument of another macro (see
[Self-Referential Macros](Self_002dReferential-Macros.md)): the
self-referential macro would be expanded once in the first scan, and a
second time in the second scan. However, this is not what happens. The
self-references that do not expand in the first scan are marked so that
they will not expand in the second scan either.

You might wonder, "Why mention the prescan, if it makes no difference?
And why not skip it and make preprocessing go faster?" The answer is
that the prescan does make a difference in three special cases:

-   Nested calls to a macro.

    We say that *nested* calls to a macro occur when a macro's argument
    contains a call to that very macro. For example, if `f` is a macro
    that expects one argument, `f (f (1))` is a nested pair of calls to
    `f`. The desired expansion is made by expanding `f (1)` and
    substituting that into the definition of `f`. The prescan causes the
    expected result to happen. Without the prescan, `f (1)` itself would
    be substituted as an argument, and the inner use of `f` would appear
    during the main scan as an indirect self-reference and would not be
    expanded.

-   Macros that call other macros that stringify or concatenate.

    If an argument is stringified or concatenated, the prescan does not
    occur. If you *want* to expand a macro, then stringify or
    concatenate its expansion, you can do that by causing one macro to
    call another macro that does the stringification or concatenation.
    For instance, if you have

    
    ``` C
    #define AFTERX(x) X_ ## x
    #define XAFTERX(x) AFTERX(x)
    #define TABLESIZE 1024
    #define BUFSIZE TABLESIZE
    ```
    

    then `AFTERX(BUFSIZE)` expands to `X_BUFSIZE`, and
    `XAFTERX(BUFSIZE)` expands to `X_1024`. (Not to `X_TABLESIZE`.
    Prescan always does a complete expansion.)

-   Macros used in arguments, whose expansions contain unshielded
    commas.

    This can cause a macro expanded on the second scan to be called with
    the wrong number of arguments. Here is an example:

    
    ``` C
    #define foo  a,b
    #define bar(x) lose(x)
    #define lose(x) (1 + (x))
    ```
    

    We would like `bar(foo)` to turn into `(1 + (foo))`, which would
    then turn into `(1 + (a,b))`. Instead, `bar(foo)` expands into
    `lose(a,b)`, which gives an error because `lose` requires a single
    argument. In this case, the problem is easily solved by the same
    parentheses that ought to be used to prevent misnesting of
    arithmetic operations:

    
    ``` C
    #define foo (a,b)
    ```

    ``` C
    or
    ```

    ``` C
    #define bar(x) lose((x))
    ```
    

    The extra pair of parentheses prevents the comma in `foo`'s
    definition from being interpreted as an argument separator.

------------------------------------------------------------------------

Previous: [Self-Referential Macros](Self_002dReferential-Macros.md),
Up: [Macro Pitfalls](Macro-Pitfalls.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
