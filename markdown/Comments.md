Next: [Identifiers](Identifiers.md), Previous:
[Whitespace](Whitespace.md), Up: [Lexical Syntax](Lexical-Syntax.md)
 
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 5.4 Comments 


A comment encapsulates text that has no effect on the program's
execution or meaning.

The purpose of comments is to explain the code to people that read it.
Writing good comments for your code is tremendously important---they
should provide background information that helps programmers understand
the reasons why the code is written the way it is. You, returning to the
code six months from now, will need the help of these comments to
remember why you wrote it this way.

Outdated comments that become incorrect are counterproductive, so part
of the software developer's responsibility is to update comments as
needed to correspond with changes to the program code.

C allows two kinds of comment syntax, the traditional style and the C++
style. A traditional C comment starts with '`/*`' and ends with
'`*/`'. For instance,

``` C
/* This is a comment in traditional C syntax. */
```

A traditional comment can contain '`/*`', but these delimiters
do not nest as pairs. The first '`*/`' ends the comment
regardless of whether it contains '`/*`' sequences.

``` C
/* This /* is a comment */ But this is not! */
```

A *line comment* starts with '`//`' and ends at the end of the
line. For instance,

``` C
// This is a comment in C++ style.
```

Line comments do nest, in effect, because '`//`' inside a line
comment is part of that comment:

``` C
// this whole line is // one comment
This is code, not comment.
```

It is safe to put line comments inside block comments, or vice versa.

``` C
/* traditional comment
   // contains line comment
   more traditional comment
 */ text here is not a comment

// line comment /* contains traditional comment */
```

But beware of commenting out one end of a traditional comment with a
line comment. The delimiter '`/*`' doesn't start a comment if
it occurs inside an already-started comment.

``` C
 // line comment  /* That would ordinarily begin a block comment.
    Oops! The line comment has ended;
    this isn't a comment any more.  */
```

Comments are not recognized within string constants. \"/\* blah \*/\" is
the string constant '`/* blah */`', not an empty string.

In this manual we show the text in comments in a variable-width font,
for readability, but this font distinction does not exist in source
files.

A comment is syntactically equivalent to whitespace, so it always
separates tokens. Thus,

``` C
  int/* comment */foo;
is equivalent to
  int foo;
```

but clean code always uses real whitespace to separate the comment
visually from surrounding code.

------------------------------------------------------------------------

Next: [Identifiers](Identifiers.md), Previous:
[Whitespace](Whitespace.md), Up: [Lexical Syntax](Lexical-Syntax.md)
 
[Contents](index.md#SEC_Contents "Table of contents")  
