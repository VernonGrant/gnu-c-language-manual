Next: [Wide Character Constants](Wide-Character-Constants.md),
Previous: [UTF-8 String Constants](UTF_002d8-String-Constants.md), Up:
[Constants](Constants.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 12.9 Unicode Character Codes 


You can specify Unicode characters, for individual character constants
or as part of string constants (see [String
Constants](String-Constants.md)), using escape sequences. Use the
'`\u`' escape sequence with a 16-bit hexadecimal Unicode
character code. If the code value is too big for 16 bits, use the
'`\U`' escape sequence with a 32-bit hexadecimal Unicode
character code. (These codes are called *universal character names*.)
For example,

``` C
\u6C34      /* 16-bit code (UTF-16) */
\U0010ABCD  /* 32-bit code (UTF-32) */
```

One way to use these is in UTF-8 string constants (see [UTF-8 String
Constants](UTF_002d8-String-Constants.md)). For instance,

``` C
u8"fóó \u6C34 \U0010ABCD"
```

You can also use them in wide character constants (see [Wide Character
Constants](Wide-Character-Constants.md)), like this:

``` C
u'\u6C34'      /* 16-bit code */
U'\U0010ABCD'  /* 32-bit code */
```

and in wide string constants (see [Wide String
Constants](Wide-String-Constants.md)), like this:

``` C
u"\u6C34\u6C33"  /* 16-bit code */
U"\U0010ABCD"    /* 32-bit code */
```

Codes in the range of `D800` through `DFFF` are not valid in Unicode.
Codes less than `00A0` are also forbidden, except for `0024`, `0040`,
and `0060`; these characters are actually ASCII control characters, and
you can specify them with other escape sequences (see [Character
Constants](Character-Constants.md)).
