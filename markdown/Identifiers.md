Next: [Operators and Punctuation](Operators_002fPunctuation.md),
Previous: [Comments](Comments.md), Up: [Lexical
Syntax](Lexical-Syntax.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 5.5 Identifiers 


An *identifier* (name) in C is a sequence of letters and digits, as well
as '`_`', that does not start with a digit. Most compilers also
allow '`$`'. An identifier can be as long as you like; for
example,

``` C
int anti_dis_establishment_arian_ism;
```


Letters in identifiers are case-sensitive in C; thus, `a` and `A` are
two different identifiers.


Identifiers in C are used as variable names, function names, typedef
names, enumeration constants, type tags, field names, and labels.
Certain identifiers in C are *keywords*, which means they have specific
syntactic meanings. Keywords in C are *reserved words*, meaning you
cannot use them in any other way. For instance, you can't define a
variable or function named `return` or `if`.

You can also include other characters, even non-ASCII characters, in
identifiers by writing their Unicode character names, which start with
'`\u`' or '`\U`', in the identifier name. See [Unicode
Character Codes](Unicode-Character-Codes.md). However, it is usually a
bad idea to use non-ASCII characters in identifiers, and when they are
written in English, they never need non-ASCII characters. See [Write
Programs in English!](English.md).

Whitespace is required to separate two consecutive identifiers, or to
separate an identifier from a preceding or following numeric constant.
