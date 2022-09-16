Next: [Integer Constant Data Types](Integer-Const-Type.md), Up:
[Constants](Constants.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 12.1 Integer Constants 


An integer constant consists of a number to specify the value, followed
optionally by suffix letters to specify the data type.

The simplest integer constants are numbers written in base 10 (decimal),
such as `5`, `77`, and `403`. A decimal constant cannot start with the
character '`0`' (zero) because that makes the constant octal.

You can get the effect of a negative integer constant by putting a minus
sign at the beginning. In grammatical terms, that is an arithmetic
expression rather than a constant, but it behaves just like a true
constant.

Integer constants can also be written in octal (base 8), hexadecimal
(base 16), or binary (base 2). An octal constant starts with the
character '`0`' (zero), followed by any number of octal digits
('`0`' to '`7`'):

``` C
0      // zero
077    // 63
0403   // 259
```

Pedantically speaking, the constant `0` is an octal constant, but we can
think of it as decimal; it has the same value either way.

A hexadecimal constant starts with '`0x`' (upper or lower case)
followed by hex digits ('`0`' to '`9`', as well as
'`a`' through '`f`' in upper or lower case):

``` C
0xff   // 255
0XA0   // 160
0xffFF // 65535
```


A binary constant starts with '`0b`' (upper or lower case)
followed by bits (each represented by the characters '`0`' or
'`1`'):

``` C
0b101  // 5
```

Binary constants are a GNU C extension, not part of the C standard.

Sometimes a space is needed after an integer constant to avoid lexical
confusion with the following tokens. See [Invalid
Numbers](Invalid-Numbers.md).

------------------------------------------------------------------------

Next: [Integer Constant Data Types](Integer-Const-Type.md), Up:
[Constants](Constants.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
