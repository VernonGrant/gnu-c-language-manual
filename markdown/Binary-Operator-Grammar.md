Next: [Order of Execution](Order-of-Execution.md), Previous:
[Execution Control Expressions](Execution-Control-Expressions.md), Up:
[GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


## 9 Binary Operator Grammar 


*Binary operators* are those that take two operands, one on the left and
one on the right.

All the binary operators in C are syntactically left-associative. This
means that `a op b op c` means `(a op b) op c`. However, the only
operators you should repeat in this way without parentheses are
'`+`', '`-`', '`*`' and '`/`',
because those cases are clear from algebra. So it is OK to write
`a + b + c` or `a - b - c`, but never `a == b == c` or `a % b % c`. For
those operators, use explicit parentheses to show how the operations
nest.

Each C operator has a *precedence*, which is its rank in the grammatical
order of the various operators. The operators with the highest
precedence grab adjoining operands first; these expressions then become
operands for operators of lower precedence.

The precedence order of operators in C is fully specified, so any
combination of operations leads to a well-defined nesting. We state only
part of the full precedence ordering here because it is bad practice for
C code to depend on the other cases. For cases not specified in this
chapter, always use parentheses to make the nesting
explicit.[^2^](#FOOT2)

You can depend on this subsequence of the precedence ordering (stated
from highest precedence to lowest):

1.  Component access ('`.`' and '`->`').
2.  Unary prefix operators.
3.  Unary postfix operators.
4.  Multiplication, division, and remainder (they have the same
    precedence).
5.  Addition and subtraction (they have the same precedence).
6.  Comparisons---but watch out!
7.  Logical operators '`&&`' and '`||`'---but watch
    out!
8.  Conditional expression with '`?`' and '`:`'.
9.  Assignments.
10. Sequential execution (the comma operator, '`,`').

Two of the lines in the above list say "but watch out!" That means that
the line covers operators with subtly different precedence. Never depend
on the grammar of C to decide how two comparisons nest; instead, always
use parentheses to specify their nesting.

You can let several '`&&`' operators associate, or several
'`||`' operators, but always use parentheses to show how
'`&&`' and '`||`' nest with each other. See [Logical
Operators](Logical-Operators.md).

There is one other precedence ordering that code can depend on:

1.  Unary postfix operators.
2.  Bitwise and shift operators---but watch out!
3.  Conditional expression with '`?`' and '`:`'.

The caveat for bitwise and shift operators is like that for logical
operators: you can let multiple uses of one bitwise operator associate,
but always use parentheses to control nesting of dissimilar operators.

These lists do not specify any precedence ordering between the bitwise
and shift operators of the second list and the binary operators above
conditional expressions in the first list. When they come together,
parenthesize them. See [Bitwise Operations](Bitwise-Operations.md).


------------------------------------------------------------------------

#### Footnotes 

##### [(2)](#DOCF2)

Personal note from Richard Stallman: I wrote GCC without remembering
anything about the C precedence order beyond what's stated here. I
studied the full precedence table to write the parser, and promptly
forgot it again. If you need to look up the full precedence order to
understand some C code, fix the code with parentheses so nobody else
needs to do that.

------------------------------------------------------------------------

Next: [Order of Execution](Order-of-Execution.md), Previous:
[Execution Control Expressions](Execution-Control-Expressions.md), Up:
[GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
