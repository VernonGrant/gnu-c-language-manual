Next: [String Constants](String-Constants.md), Previous: [Invalid
Numbers](Invalid-Numbers.md), Up: [Constants](Constants.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 12.6 Character Constants 


A *character constant* is written with single quotes, as in `'c'`. In
the simplest case, `c` is a single ASCII character that the
constant should represent. The constant has type `int`, and its value is
the character code of that character. For instance, `'a'` represents the
character code for the letter '`a`': 97, that is.

To put the '`'`' character (single quote) in the character
constant, *escape* it with a backslash ('`\`'). This character
constant looks like `'\''`. The backslash character here functions as an
*escape character*, and such a sequence, starting with '`\`',
is called an *escape sequence*.

To put the '`\`' character (backslash) in the character
constant, escape it with '`\`' (another backslash). This
character constant looks like `'\\'`.


Here are all the escape sequences that represent specific characters in
a character constant. The numeric values shown are the corresponding
ASCII character codes, as decimal numbers.

``` C
'\a' ⇒ 7       /* alarm, CTRL-g */
'\b' ⇒ 8       /* backspace, BS, CTRL-h */
'\t' ⇒ 9       /* tab, TAB, CTRL-i */
'\n' ⇒ 10      /* newline, CTRL-j */
'\v' ⇒ 11      /* vertical tab, CTRL-k */
'\f' ⇒ 12      /* formfeed, CTRL-l */
'\r' ⇒ 13      /* carriage return, RET, CTRL-m */
'\e' ⇒ 27      /* escape character, ESC, CTRL-[ */
'\\' ⇒ 92      /* backslash character, \ */
'\'' ⇒ 39      /* single quote character, ' */
'\"' ⇒ 34      /* double quote character, " */
'\?' ⇒ 63      /* question mark, ? */
```

'`\e`' is a GNU C extension; to stick to standard C, write
'`\33`'. (The number after '`backslash`' is octal.) To
specify a character constant using decimal, use a cast; for instance,
`(unsigned char) 27`.

You can also write octal and hex character codes as
'`\octalcode`' or '`\xhexcode`'. Decimal is not an
option here, so octal codes do not need to start with '`0`'.

The character constant's value has type `int`. However, the character
code is treated initially as a `char` value, which is then converted to
`int`. If the character code is greater than 127 (`0177` in octal), the
resulting `int` may be negative on a platform where the type `char` is 8
bits long and signed.

------------------------------------------------------------------------

Next: [String Constants](String-Constants.md), Previous: [Invalid
Numbers](Invalid-Numbers.md), Up: [Constants](Constants.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
