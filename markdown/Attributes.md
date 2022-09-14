Next: [Signals](Signals.md), Previous: [Digraphs](Digraphs.md), Up:
[GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


## Appendix D Attributes in Declarations 


You can specify certain additional requirements in a declaration, to get
fine-grained control over code generation, and helpful informational
messages during compilation. We use a few attributes in code examples
throughout this manual, including

`aligned`

-   The `aligned` attribute specifies a minimum alignment for a variable
    or structure field, measured in bytes:

    
    ``` C
    int foo __attribute__ ((aligned (8))) = 0;
    ```
    

    This directs GNU C to allocate `foo` at an address that is a
    multiple of 8 bytes. However, you can't force an alignment bigger
    than the computer's maximum meaningful alignment.

`packed`

-   The `packed` attribute specifies to compact the fields of a
    structure by not leaving gaps between fields. For example,

    
    ``` C
    struct __attribute__ ((packed)) bar
    {
      char a;
      int b;
    };
    ```
    

    allocates the integer field `b` at byte 1 in the structure,
    immediately after the character field `a`. The packed structure is
    just 5 bytes long (assuming `int` is 4 bytes) and its alignment is
    1, that of `char`.

`deprecated`

-   Applicable to both variables and functions, the `deprecated`
    attribute tells the compiler to issue a warning if the variable or
    function is ever used in the source file.

    
    ``` C
    int old_foo __attribute__ ((deprecated));

    int old_quux () __attribute__ ((deprecated));
    ```
    

`__noinline__`

-   The `__noinline__` attribute, in a function's declaration or
    definition, specifies never to inline calls to that function. All
    calls to that function, in a compilation unit where it has this
    attribute, will be compiled to invoke the separately compiled
    function. See [Inline Function
    Definitions](Inline-Function-Definitions.md).

`__noclone__`

-   The `__noclone__` attribute, in a function's declaration or
    definition, specifies never to clone that function. Thus, there will
    be only one compiled version of the function. See [Label Value
    Caveats](Label-Value-Caveats.md), for more information about
    cloning.

`always_inline`

-   The `always_inline` attribute, in a function's declaration or
    definition, specifies to inline all calls to that function (unless
    something about the function makes inlining impossible). This
    applies to all calls to that function in a compilation unit where it
    has this attribute. See [Inline Function
    Definitions](Inline-Function-Definitions.md).

`gnu_inline`

-   The `gnu_inline` attribute, in a function's declaration or
    definition, specifies to handle the `inline` keyword the way GNU C
    originally implemented it, many years before ISO C said anything
    about inlining. See [Inline Function
    Definitions](Inline-Function-Definitions.md).

For full documentation of attributes, see the GCC manual. See [System
Headers](https://gcc.gnu.org/onlinedocs/gcc/Attribute-Syntax.md#Attribute-Syntax)
in Using the GNU Compiler Collection.

------------------------------------------------------------------------

Next: [Signals](Signals.md), Previous: [Digraphs](Digraphs.md), Up:
[GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
