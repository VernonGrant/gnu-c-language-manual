Next: [Concatenation](Concatenation.md), Previous: [Macro
Arguments](Macro-Arguments.md), Up: [Macros](Macros.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 26.5.4 Stringification 


Sometimes you may want to convert a macro argument into a string
constant. Parameters are not replaced inside string constants, but you
can use the `#` preprocessing operator instead. When a macro parameter
is used with a leading `#`, preprocessing replaces it with the literal
text of the actual argument, converted to a string constant. Unlike
normal parameter replacement, the argument is not macro-expanded first.
This is called *stringification*.

There is no way to combine an argument with surrounding text and
stringify it all together. But you can write a series of string
constants and stringified arguments. After preprocessing replaces the
stringified arguments with string constants, the consecutive string
constants will be concatenated into one long string constant (see
[String Constants](String-Constants.md)).

Here is an example that uses stringification and concatenation of string
constants:

``` C
#define WARN_IF(EXP) \
  do { if (EXP) \
          fprintf (stderr, "Warning: " #EXP "\n"); } \
  while (0)

WARN_IF (x == 0);
     →
  do { if (x == 0)
          fprintf (stderr, "Warning: " "x == 0" "\n"); }
  while (0);
```

The argument for `EXP` is substituted once, as is, into the `if`
statement, and once, stringified, into the argument to `fprintf`. If `x`
were a macro, it would be expanded in the `if` statement but not in the
string.

The `do` and `while (0)` are a kludge to make it possible to write
`WARN_IF (arg);`. The resemblance of `WARN_IF` to a function makes that
a natural way to write it. See [Swallowing the
Semicolon](Swallowing-the-Semicolon.md).

Stringification in C involves more than putting double-quote characters
around the fragment. It also backslash-escapes the quotes surrounding
embedded string constants, and all backslashes within string and
character constants, in order to get a valid C string constant with the
proper contents. Thus, stringifying `p = "foo\n";` results in
\"p = \\\"foo\\\\n\\\";\". However, backslashes that are not inside
string or character constants are not duplicated: '`\n`' by
itself stringifies to \"\\n\".

All leading and trailing whitespace in text being stringified is
ignored. Any sequence of whitespace in the middle of the text is
converted to a single space in the stringified result. Comments are
replaced by whitespace long before stringification happens, so they
never appear in stringified text.

There is no way to convert a macro argument into a character constant.

To stringify the result of expansion of a macro argument, you have to
use two levels of macros, like this:

``` C
#define xstr(S) str(S)
#define str(s) #s
#define foo 4
str (foo)
     → "foo"
xstr (foo)
     → xstr (4)
     → str (4)
     → "4"
```

`s` is stringified when it is used in `str`, so it is not macro-expanded
first. But `S` is an ordinary argument to `xstr`, so it is completely
macro-expanded before `xstr` itself is expanded (see [Argument
Prescan](Argument-Prescan.md)). Therefore, by the time `str` gets to
its argument text, that text already been macro-expanded.

------------------------------------------------------------------------

Next: [Concatenation](Concatenation.md), Previous: [Macro
Arguments](Macro-Arguments.md), Up: [Macros](Macros.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
