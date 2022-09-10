Next: [Unicode Character Codes](Unicode-Character-Codes.md), Previous:
[String Constants](String-Constants.md), Up:
[Constants](Constants.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 12.8 UTF-8 String Constants 


Writing '`u8`' immediately before a string constant, with no
intervening space, means to represent that string in UTF-8 encoding as a
sequence of bytes. UTF-8 represents ASCII characters with a single byte,
and represents non-ASCII Unicode characters (codes 128 and up) as
multibyte sequences. Here is an example of a UTF-8 constant:

``` C
u8"A cónstàñt"
```

This constant occupies 13 bytes plus the terminating null, because each
of the accented letters is a two-byte sequence.

Concatenating an ordinary string with a UTF-8 string conceptually
produces another UTF-8 string. However, if the ordinary string contains
character codes 128 and up, the results cannot be relied on.
