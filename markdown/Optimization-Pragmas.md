Previous: [Severity Pragmas](Severity-Pragmas.md), Up:
[Pragmas](Pragmas.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 30.1.3 Optimization Pragmas 

These pragmas enable a particular optimization for specific function
definitions. The settings take effect at the end of a function
definition, so the clean place to use these pragmas is between function
definitions.

`#pragma GCC optimize optimization`\
`_Pragma ("GCC optimize optimization")`

-   These pragmas enable the optimization `optimization` for
    the following functions. For example,

    
    ``` C
    _Pragma ("GCC optimize -fforward-propagate")
    ```
    

    says to apply the '`forward-propagate`' optimization to all
    following function definitions. Specifying optimizations for
    individual functions, rather than for the entire program, is rare
    but can be useful for getting around a bug in the compiler.

    If `optimization` does not correspond to a defined
    optimization option, the pragma is erroneous. To turn off an
    optimization, use the corresponding '`-fno-`' option, such
    as '`-fno-forward-propagate`'.

`#pragma GCC target optimizations`\
`_Pragma ("GCC target optimizations")`

-   The pragma '`GCC target`' is similar to
    '`GCC optimize`' but is used for platform-specific
    optimizations. Thus,

    
    ``` C
    _Pragma ("GCC target popcnt")
    ```
    

    activates the optimization '`popcnt`' for all following
    function definitions. This optimization is supported on a few common
    targets but not on others.

`#pragma GCC push_options`\
`_Pragma ("GCC push_options")`

-   The '`push_options`' pragma saves on a stack the current
    settings specified with the '`target`' and
    '`optimize`' pragmas.

`#pragma GCC pop_options`\
`_Pragma ("GCC pop_options")`

-   The '`pop_options`' pragma pops saved settings from that
    stack.

    Here's an example of using this stack.

    
    ``` C
    _Pragma ("GCC push_options")
    _Pragma ("GCC optimize forward-propagate")

    /* Functions to compile
       with the forward-propagate optimization. */

    _Pragma ("GCC pop_options")
    /* Ends enablement of forward-propagate. */
    ```
    

`#pragma GCC reset_options`\
`_Pragma ("GCC reset_options")`

-   Clears all pragma-defined '`target`' and
    '`optimize`' optimization settings.

------------------------------------------------------------------------

Previous: [Severity Pragmas](Severity-Pragmas.md), Up:
[Pragmas](Pragmas.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
