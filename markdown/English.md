Next: [Characters](Characters.md), Up: [Lexical
Syntax](Lexical-Syntax.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 5.1 Write Programs in English! 

In principle, you can write the function and variable names in a
program, and the comments, in any human language. C allows any kinds of
characters in comments, and you can put non-ASCII characters into
identifiers with a special prefix. However, to enable programmers in all
countries to understand and develop the program, it is best given
today's circumstances to write identifiers and comments in English.

English is the one language that programmers in all countries generally
study. If a program's names are in English, most programmers in
Bangladesh, Belgium, Bolivia, Brazil, and Bulgaria can understand them.
Most programmers in those countries can speak English, or at least read
it, but they do not read each other's languages at all. In India, with
so many languages, two programmers may have no common language other
than English.

If you don't feel confident in writing English, do the best you can, and
follow each English comment with a version in a language you write
better; add a note asking others to translate that to English. Someone
will eventually do that.

The program's user interface is a different matter. We don't need to
choose one language for that; it is easy to support multiple languages
and let each user choose the language to use. This requires writing the
program to support localization of its interface. (The `gettext` package
exists to support this; see [The GNU C
Library](https://www.gnu.org/software/libc/manual/html_node/Message-Translation.md#Message-Translation)
in The GNU C Library Reference Manual.) Then a community-based
translation effort can provide support for all the languages users want
to use.
