Next: [Whitespace](Whitespace.md), Previous: [Write Programs in
English!](English.md), Up: [Lexical Syntax](Lexical-Syntax.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 5.2 Characters 


GNU C source files are usually written in the
[ASCII](https://en.wikipedia.org/wiki/ASCII) character set, which was
defined in the 1960s for English. However, they can also include Unicode
characters represented in the
[UTF-8](https://en.wikipedia.org/wiki/UTF-8) multibyte encoding. This
makes it possible to represent accented letters such as '`á`',
as well as other scripts such as Arabic, Chinese, Cyrillic, Hebrew,
Japanese, and Korean.[^1^](#FOOT1)

In C source code, non-ASCII characters are valid in comments, in wide
character constants (see [Wide Character
Constants](Wide-Character-Constants.md)), and in string constants (see
[String Constants](String-Constants.md)).

Another way to specify non-ASCII characters in constants (character or
string) and identifiers is with an escape sequence starting with
backslash, specifying the intended Unicode character. (See [Unicode
Character Codes](Unicode-Character-Codes.md).) This specifies
non-ASCII characters without putting a real non-ASCII character in the
source file itself.

C accepts two-character aliases called *digraphs* for certain
characters. See [Digraphs](Digraphs.md).


------------------------------------------------------------------------

#### Footnotes 

##### [(1)](#DOCF1)

On some obscure systems, GNU C uses UTF-EBCDIC instead of UTF-8, but
that is not worth describing in this manual.
