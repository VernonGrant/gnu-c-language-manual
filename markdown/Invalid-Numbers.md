Next: [Character Constants](Character-Constants.md), Previous:
[Imaginary Constants](Imaginary-Constants.md), Up:
[Constants](Constants.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 12.5 Invalid Numbers 

Some number-like constructs which are not really valid as numeric
constants are treated as numbers in preprocessing directives. If these
constructs appear outside of preprocessing, they are erroneous. See
[Preprocessing Tokens](Preprocessing-Tokens.md).

Sometimes we need to insert spaces to separate tokens so that they won't
be combined into a single number-like construct. For example, `0xE+12`
is a preprocessing number that is not a valid numeric constant, so it is
a syntax error. If what we want is the three tokens `0xE + 12`, we have
to use those spaces as separators.
