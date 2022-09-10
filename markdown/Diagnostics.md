Next: [Line Control](Line-Control.md), Previous:
[Conditionals](Conditionals.md), Up:
[Preprocessing](Preprocessing.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 26.7 Diagnostics 


The directive `#error` reports a fatal error. The tokens forming the
rest of the line following `#error` are used as the error message.

The usual place to use `#error` is inside a conditional that detects a
combination of parameters that you know the program does not properly
support. For example,

``` C
#if !defined(UNALIGNED_INT_ASM_OP) && defined(DWARF2_DEBUGGING_INFO)
#error "DWARF2_DEBUGGING_INFO requires UNALIGNED_INT_ASM_OP."
#endif
```


The directive `#warning` is like `#error`, but it reports a warning
instead of an error. The tokens following `#warning` are used as the
warning message.

You might use `#warning` in obsolete header files, with a message saying
which header file to use instead.

Neither `#error` nor `#warning` macro-expands its argument. Internal
whitespace sequences are each replaced with a single space. The line
must consist of complete tokens. It is wisest to make the argument of
these directives be a single string constant; this avoids problems with
apostrophes and the like.
