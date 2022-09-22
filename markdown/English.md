Next: [Characters](Characters.md), Up: [Lexical
Syntax](Lexical-Syntax.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 5.1 Write Programs in English! 

In principle, you can write the function and variable names in a
program, and the comments, in any human language. C allows any kinds of
Unicode characters in comments, and you can put them into identifiers
with a special prefix (see [Unicode Character
Codes](Unicode-Character-Codes.md)). However, to enable programmers in
all countries to understand and develop the program, it is best under
today's circumstances to write all identifiers and comments in English.

English is the common language of programmers; in all countries,
programmers generally learn English. If names and comments in a program
are written in English, most programmers in Bangladesh, Belgium,
Bolivia, Brazil, Bulgaria and Burundi can understand them. In all those
countries, most programmers can speak English, or at least read it, but
they do not read each other's languages at all. In India, with so many
languages, two programmers may have no common language other than
English.

If you don't feel confident in writing English, do the best you can, and
follow each English comment with a version in a language you write
better; add a note asking others to translate that to English. Someone
will eventually do that.

The program's user interface is a different matter. We don't need to
choose one language for that; it is easy to support multiple languages
and let each user choose the language for display. This requires writing
the program to support localization of its interface. (The `gettext`
package exists to support this; see [The GNU C
Library](https://www.gnu.org/software/libc/manual/html_node/Message-Translation.md#Message-Translation)
in The GNU C Library Reference Manual.) Then a community-based
translation effort can provide support for all the languages users want
to use.

------------------------------------------------------------------------

Next: [Characters](Characters.md), Up: [Lexical
Syntax](Lexical-Syntax.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
