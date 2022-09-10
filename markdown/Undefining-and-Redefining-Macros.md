Next: [Directives Within Macro
Arguments](Directives-Within-Macro-Arguments.md), Previous:
[Predefined Macros](Predefined-Macros.md), Up: [Macros](Macros.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.5.8 Undefining and Redefining Macros 


You can *undefine* a macro with the `#undef` directive. `#undef` takes a
single argument, the name of the macro to undefine. You use the bare
macro name, even if the macro is function-like. It is an error if
anything appears on the line after the macro name. `#undef` has no
effect if the name is not a macro.

``` C
#define FOO 4
x = FOO;        → x = 4;
#undef FOO
x = FOO;        → x = FOO;
```

Once a macro has been undefined, that identifier may be *redefined* as a
macro by a subsequent `#define` directive. The new definition need not
have any resemblance to the old definition.

You can define a macro again without first undefining it only if the new
definition is *effectively the same* as the old one. Two macro
definitions are effectively the same if:

-   Both are the same type of macro (object- or function-like).
-   All the tokens of the replacement list are the same.
-   If there are any parameters, they are the same.
-   Whitespace appears in the same places in both. It need not be
    exactly the same amount of whitespace, though. Remember that
    comments count as whitespace.

These definitions are effectively the same:

``` C
#define FOUR (2 + 2)
#define FOUR         (2    +    2)
#define FOUR (2 /* two */ + 2)
```

but these are not:

``` C
#define FOUR (2 + 2)
#define FOUR ( 2+2 )
#define FOUR (2 * 2)
#define FOUR(score,and,seven,years,ago) (2 + 2)
```

This allows two different header files to define a common macro.

You can redefine an existing macro with #define, but redefining an
existing macro name with a different definition results in a warning.

------------------------------------------------------------------------

Next: [Directives Within Macro
Arguments](Directives-Within-Macro-Arguments.md), Previous:
[Predefined Macros](Predefined-Macros.md), Up: [Macros](Macros.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
