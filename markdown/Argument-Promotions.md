Next: [Operand Promotions](Operand-Promotions.md), Previous:
[Assignment Type Conversions](Assignment-Type-Conversions.md), Up:
[Type Conversions](Type-Conversions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 24.3 Argument Promotions 


When a function's definition or declaration does not specify the type of
an argument, that argument is passed without conversion in whatever type
it has, with these exceptions:

-   Some narrow numeric values are *promoted* to a wider type. If the
    expression is a narrow integer, such as `char` or `short`, the call
    converts it automatically to `int` (see [Integer Data
    Types](Integer-Types.md)).[^8^](#FOOT8)

    In this example, the expression `c` is passed as an `int`:

    
    ``` C
    char c = '$';

    printf ("Character c is '%c'\n", c);
    ```
    

-   If the expression has type `float`, the call converts it
    automatically to `double`.

-   An array as argument is converted to a pointer to its zeroth
    element.

-   A function name as argument is converted to a pointer to that
    function.


------------------------------------------------------------------------

#### Footnotes 

##### [(8)](#DOCF8)

On an embedded controller where `char` or `short` is the same width as
`int`, `unsigned char` or `unsigned short` promotes to `unsigned int`,
but that never occurs in GNU C on real computers.
