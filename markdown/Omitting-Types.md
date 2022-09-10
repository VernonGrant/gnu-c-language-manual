Previous: [`auto` and `register`](auto-and-register.md), Up:
[Variables](Variables.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 20.11 Omitting Types in Declarations 


The syntax of C traditionally allows omitting the data type in a
declaration if it specifies a storage class, a type qualifier (see the
next chapter), or `auto` or `register`. Then the type defaults to `int`.
For example:

``` C
auto foo = 42;
```

This is bad practice; if you see it, fix it.
