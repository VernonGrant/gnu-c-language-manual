Next: [Comments](Comments.md), Previous:
[Characters](Characters.md), Up: [Lexical Syntax](Lexical-Syntax.md)
 
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 5.3 Whitespace 


Whitespace means characters that exist in a file but appear blank in a
printed listing of a file (or traditionally did appear blank, several
decades ago). The C language requires whitespace in order to separate
two consecutive identifiers, or to separate an identifier from a numeric
constant. Other than that, and a few special situations described later,
whitespace is optional; you can put it in when you wish, to make the
code easier to read.

Space and tab in C code are treated as whitespace characters. So are
line breaks. You can represent a line break with the newline character
(also called *linefeed* or LF), CR (carriage return), or the CRLF
sequence (two characters: carriage return followed by a newline
character).

The *formfeed* character, Control-L, was traditionally used to divide a
file into pages. It is still used this way in source code, and the tools
that generate nice printouts of source code still start a new page after
each "formfeed" character. Dividing code into pages separated by
formfeed characters is a good way to break it up into comprehensible
pieces and show other programmers where they start and end.

The *vertical tab* character, Control-K, was traditionally used to make
printing advance down to the next section of a page. We know of no
particular reason to use it in source code, but it is still accepted as
whitespace in C.

Comments are also syntactically equivalent to whitespace.
