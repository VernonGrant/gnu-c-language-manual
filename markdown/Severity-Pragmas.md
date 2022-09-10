Next: [Optimization Pragmas](Optimization-Pragmas.md), Previous:
[Pragma Basics](Pragma-Basics.md), Up: [Pragmas](Pragmas.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 30.1.2 Severity Pragmas 

These pragmas control the severity of classes of diagnostics. You can
specify the class of diagnostic with the GCC option that causes those
diagnostics to be generated.

`#pragma GCC diagnostic error option`\
`_Pragma ("GCC diagnostic error option")`

-   For code following this pragma, treat diagnostics of the variety
    specified by `option`{.variable} as errors. For example:

    
    ``` C
    _Pragma ("GCC diagnostic error -Wformat")
    ```
    

    specifies to treat diagnostics enabled by the `-Wformat`{.variable}
    option as errors rather than warnings.

`#pragma GCC diagnostic warning option`\
`_Pragma ("GCC diagnostic warning option")`

-   For code following this pragma, treat diagnostics of the variety
    specified by `option`{.variable} as warnings. This overrides the
    `-Werror`{.variable} option which says to treat warnings as errors.

`#pragma GCC diagnostic ignore option`\
`_Pragma ("GCC diagnostic ignore option")`

-   For code following this pragma, refrain from reporting any
    diagnostics of the variety specified by `option`{.variable}.

`#pragma GCC diagnostic push`\
`_Pragma ("GCC diagnostic push")`\
`#pragma GCC diagnostic pop`\
`_Pragma ("GCC diagnostic pop")`

-   These pragmas maintain a stack of states for severity settings.
    '`GCC diagnostic push`' saves the current settings on the
    stack, and '`GCC diagnostic pop`' pops the last stack item
    and restores the current settings from that.

    '`GCC diagnostic pop`' when the severity setting stack is
    empty restores the settings to what they were at the start of
    compilation.

    Here is an example:

    
    ``` C
    _Pragma ("GCC diagnostic error -Wformat")

    /* -Wformat messages treated as errors.  */

    _Pragma ("GCC diagnostic push")
    _Pragma ("GCC diagnostic warning -Wformat")

    /* -Wformat messages treated as warnings.  */

    _Pragma ("GCC diagnostic push")
    _Pragma ("GCC diagnostic ignored -Wformat")

    /* -Wformat messages suppressed.  */

    _Pragma ("GCC diagnostic pop")

    /* -Wformat messages treated as warnings again.  */

    _Pragma ("GCC diagnostic pop")

    /* -Wformat messages treated as errors again.  */

    /* This is an excess ‘pop’ that matches no ‘push’.  */
    _Pragma ("GCC diagnostic pop")

    /* -Wformat messages treated once again
       as specified by the GCC command-line options.  */
    ```
    

------------------------------------------------------------------------

Next: [Optimization Pragmas](Optimization-Pragmas.md), Previous:
[Pragma Basics](Pragma-Basics.md), Up: [Pragmas](Pragmas.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
