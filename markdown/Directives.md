Next: [Preprocessing Tokens](Preprocessing-Tokens.md), Previous:
[Preprocessing Overview](Preproc-Overview.md), Up:
[Preprocessing](Preprocessing.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 26.2 Directives 


*Preprocessing directives* are lines in the program that start with
'`#`'. Whitespace is allowed before and after the
'`#`'. The '`#`' is followed by an identifier, the
*directive name*. It specifies the operation to perform. Here are a
couple of examples:

``` C
#define LIMIT 51
  #   undef LIMIT
# error You screwed up!
```

We usually refer to a directive as `#name` where `name` is
the directive name. For example, `#define` means the directive that
defines a macro.

The '`#`' that begins a directive cannot come from a macro
expansion. Also, the directive name is not macro expanded. Thus, if
`foo` is defined as a macro expanding to `define`, that does not make
`#foo` a valid preprocessing directive.

The set of valid directive names is fixed. Programs cannot define new
preprocessing directives.

Some directives require arguments; these make up the rest of the
directive line and must be separated from the directive name by
whitespace. For example, `#define` must be followed by a macro name and
the intended expansion of the macro.

A preprocessing directive cannot cover more than one line. The line can,
however, be continued with backslash-newline, or by a
'`/*…*/`'-style comment that extends past the end of the line.
These will be replaced (by nothing, or by whitespace) before the
directive is processed.
