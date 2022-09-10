Next: [Argument Promotions](Argument-Promotions.md), Previous:
[Explicit Type Conversion](Explicit-Type-Conversion.md), Up: [Type
Conversions](Type-Conversions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 24.2 Assignment Type Conversions 


Certain type conversions occur automatically in assignments and certain
other contexts. These are the conversions assignments can do:

-   Converting any numeric type to any other numeric type.
-   Converting `void *` to any other pointer type (except
    pointer-to-function types).
-   Converting any other pointer type to `void *`. (except
    pointer-to-function types).
-   Converting 0 (a null pointer constant) to any pointer type.
-   Converting any pointer type to `bool`. (The result is 1 if the
    pointer is not null.)
-   Converting between pointer types when the left-hand target type is
    upward compatible with the right-hand target type. See [Compatible
    Types](Compatible-Types.md).

These type conversions occur automatically in certain contexts, which
are:

-   An assignment converts the type of the right-hand expression to the
    type wanted by the left-hand expression. For example,

    
    ``` C
    double i;
    i = 5;
    ```
    

    converts 5 to `double`.

-   A function call, when the function specifies the type for that
    argument, converts the argument value to that type. For example,

    
    ``` C
    void foo (double);
    foo (5);
    ```
    

    converts 5 to `double`.

-   A `return` statement converts the specified value to the type that
    the function is declared to return. For example,

    
    ``` C
    double
    foo ()
    {
      return 5;
    }
    ```
    

    also converts 5 to `double`.

In all three contexts, if the conversion is impossible, that constitutes
an error.
