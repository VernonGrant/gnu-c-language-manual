Next: [Wide String Constants](Wide-String-Constants.md), Previous:
[Unicode Character Codes](Unicode-Character-Codes.md), Up:
[Constants](Constants.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 12.10 Wide Character Constants 


A *wide character constant* represents characters with more than 8 bits
of character code. This is an obscure feature that we need to document
but that you probably won't ever use. If you're just learning C, you may
as well skip this section.

The original C wide character constant looks like '`L`' (upper
case!) followed immediately by an ordinary character constant (with no
intervening space). Its data type is `wchar_t`, which is an alias
defined in `stddef.h` for one of the standard integer types.
Depending on the platform, it could be 16 bits or 32 bits. If it is 16
bits, these character constants use the UTF-16 form of Unicode; if 32
bits, UTF-32.

There are also Unicode wide character constants which explicitly specify
the width. These constants start with '`u`' or '`U`'
instead of '`L`'. '`u`' specifies a 16-bit Unicode
wide character constant, and '`U`' a 32-bit Unicode wide
character constant. Their types are, respectively, `char16_t` and
`char32_t`; they are declared in the header file `uchar.h`.
These character constants are valid even if `uchar.h` is not
included, but some uses of them may be inconvenient without including it
to declare those type names.

The character represented in a wide character constant can be an
ordinary ASCII character. `L'a'`, `u'a'` and `U'a'` are all valid, and
they are all equal to `'a'`.

In all three kinds of wide character constants, you can write a
non-ASCII Unicode character in the constant itself; the constant's value
is the character's Unicode character code. Or you can specify the
Unicode character with an escape sequence (see [Unicode Character
Codes](Unicode-Character-Codes.md)).

------------------------------------------------------------------------

Next: [Wide String Constants](Wide-String-Constants.md), Previous:
[Unicode Character Codes](Unicode-Character-Codes.md), Up:
[Constants](Constants.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
