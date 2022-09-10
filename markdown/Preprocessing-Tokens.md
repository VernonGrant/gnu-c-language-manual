Next: [Header Files](Header-Files.md), Previous:
[Directives](Directives.md), Up: [Preprocessing](Preprocessing.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 26.3 Preprocessing Tokens 


Preprocessing divides C code (minus its comments) into *tokens* that are
similar to C tokens, but not exactly the same. Here are the quirks of
preprocessing tokens.

The main classes of preprocessing tokens are identifiers, preprocessing
numbers, string constants, character constants, and punctuators; there
are a few others too.

identifier [¶](#index-identifiers-1){.copiable-anchor}

-   An *identifier* preprocessing token is syntactically like an
    identifier in C: any sequence of letters, digits, or underscores, as
    well as non-ASCII characters represented using '`\U`' or
    '`\u`', that doesn't begin with a digit.

    During preprocessing, the keywords of C have no special
    significance; at that stage, they are simply identifiers. Thus, you
    can define a macro whose name is a keyword. The only identifier that
    is special during preprocessing is `defined` (see [The `defined`
    test](defined.md)).

preprocessing number [¶](#index-numbers_002c-preprocessing){.copiable-anchor}

-   []

    A *preprocessing number* is something that preprocessing treats
    textually as a number, including C numeric constants, and other
    sequences of characters which resemble numeric constants.
    Preprocessing does not try to verify that a preprocessing number is
    a valid number in C, and indeed it need not be one.

    More precisely, preprocessing numbers begin with an optional period,
    a required decimal digit, and then continue with any sequence of
    letters, digits, underscores, periods, and exponents. Exponents are
    the two-character sequences '`e+`', '`e-`',
    '`E+`', '`E-`', '`p+`', '`p-`',
    '`P+`', and '`P-`'. (The exponents that begin with
    '`p`' or '`P`' are new to C99. They are used for
    hexadecimal floating-point constants.)

    The reason behind this unusual syntactic class is that the full
    complexity of numeric constants is irrelevant during preprocessing.
    The distinction between lexically valid and invalid floating-point
    numbers, for example, doesn't matter at this stage. The use of
    preprocessing numbers makes it possible to split an identifier at
    any position and get exactly two tokens, and reliably paste them
    together using the `##` operator (see
    [Concatenation](Concatenation.md)).

punctuator

-   A *punctuator* is syntactically like an operator. These are the
    valid punctuators:

    
    ``` C
    [  ]   (  )  {  }  .  ->
    ++ --  &  *  +  -  ~  !
    /  %   << >> <  >  <= >=  ==  !=  ^  |  &&  ||
    ?  :   ;  ...
    =  *=  /=  %=  +=  -=  <<=  >>=  &=  ^=  |=
    ,  #   ##
    <: :>  <% %>  %:  %:%:
    ```
    

string constant

-   A string constant in the source code is recognized by preprocessing
    as a single preprocessing token.

character constant

-   A character constant in the source code is recognized by
    preprocessing as a single preprocessing token.

header name

-   Within the `#include` directive, preprocessing recognizes a *header
    name* token. It consists of '`"name"`', where
    `name`{.variable} is a sequence of source characters other than
    newline and '`"`', or '`<name>`', where
    `name`{.variable} is a sequence of source characters other than
    newline and '`>`'.

    In practice, it is more convenient to think that the `#include` line
    is exempt from tokenization.

other

-   Any other character that's valid in a C source program is treated as
    a separate preprocessing token.

Once the program is broken into preprocessing tokens, they remain
separate until the end of preprocessing. Macros that generate two
consecutive tokens insert whitespace to keep them separate, if
necessary. For example,

``` C
#define foo() bar
foo()baz
     → bar baz
not
     → barbaz
```

The only exception is with the `##` preprocessing operator, which pastes
tokens together (see [Concatenation](Concatenation.md)).

Preprocessing treats the null character (code 0) as whitespace, but
generates a warning for it because it may be invisible to the user (many
terminals do not display it at all) and its presence in the file is
probably a mistake.

------------------------------------------------------------------------

Next: [Header Files](Header-Files.md), Previous:
[Directives](Directives.md), Up: [Preprocessing](Preprocessing.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
