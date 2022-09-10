Previous: [Operators and Punctuation](Operators_002fPunctuation.md),
Up: [Lexical Syntax](Lexical-Syntax.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 5.7 Line Continuation 


The sequence of a backslash and a newline is ignored absolutely anywhere
in a C program. This makes it possible to split a single source line
into multiple lines in the source file. GNU C tolerates and ignores
other whitespace between the backslash and the newline. In particular,
it always ignores a CR (carriage return) character there, in case some
text editor decided to end the line with the CRLF sequence.

The main use of line continuation in C is for macro definitions that
would be inconveniently long for a single line (see
[Macros](Macros.md)).

It is possible to continue a line comment onto another line with
backslash-newline. You can put backslash-newline in the middle of an
identifier, even a keyword, or an operator. You can even split
'`/*`', '`*/`', and '`//`' onto multiple
lines with backslash-newline. Here's an ugly example:

``` C
/\
*
*/ fo\
o +\
= 1\
0;
```

That's equivalent to '`/* */ foo += 10;`'.

Don't do those things in real programs, since they make code hard to
read.

**Note:** For the sake of using certain tools on the source code, it is
wise to end every source file with a newline character which is not
preceded by a backslash, so that it really ends the last line.
