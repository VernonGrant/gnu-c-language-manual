Next: [Integer Variations](Integer-Variations.md), Previous:
[Conversion among Integer Types](Integer-Conversion.md), Up: [Integer
Data Types](Integer-Types.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 11.1.5 Boolean Type 


The unsigned integer type `bool` holds truth values: its possible values
are 0 and 1. Converting any nonzero value to `bool` results in 1. For
example:

``` C
bool a = 0;
bool b = 1;
bool c = 4; /* Stores the value 1 in c.  */
```

Unlike `int`, `bool` is not a keyword. It is defined in the header file
`stdbool.h`.
