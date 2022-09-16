Next: [Floating-Point Constants](Floating-Constants.md), Previous:
[Integer Constants](Integer-Constants.md), Up:
[Constants](Constants.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 12.2 Integer Constant Data Types 


The type of an integer constant is normally `int`, if the value fits in
that type, but here are the complete rules. The type of an integer
constant is the first one in this sequence that can properly represent
the value,

1.  `int`
2.  `unsigned int`
3.  `long int`
4.  `unsigned long int`
5.  `long long int`
6.  `unsigned long long int`

and that isn't excluded by the following rules.

If the constant has '`l`' or '`L`' as a suffix, that
excludes the first two types (non-`long`).

If the constant has '`ll`' or '`LL`' as a suffix, that
excludes first four types (non-`long long`).

If the constant has '`u`' or '`U`' as a suffix, that
excludes the signed types.

Otherwise, if the constant is decimal (not binary, octal, or
hexadecimal), that excludes the unsigned types.

Here are some examples of the suffixes.

``` C
3000000000u      // three billion as unsigned int.
0LL              // zero as a long long int.
0403l            // 259 as a long int.
```

Suffixes in integer constants are rarely used. When the precise type is
important, it is cleaner to convert explicitly (see [Explicit Type
Conversion](Explicit-Type-Conversion.md)).

See [Integer Data Types](Integer-Types.md).
