Next: [Conditional Operator Branches](Conditional-Branches.md), Up:
[Conditional Expression](Conditional-Expression.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


#### 8.4.1 Rules for the Conditional Operator 

The first operand, `condition`, should be a value that can be
compared with zero---a number or a pointer. If it is true (nonzero),
then the conditional expression computes `iftrue` and its
value becomes the value of the conditional expression. Otherwise the
conditional expression computes `iffalse` and its value
becomes the value of the conditional expression. The conditional
expression always computes just one of `iftrue` and
`iffalse`, never both of them.

Here's an example: the absolute value of a number `x` can be written as
`(x >= 0 ? x : -x)`.

**Warning:** The conditional expression operators have rather low
syntactic precedence. Except when the conditional expression is used as
an argument in a function call, write parentheses around it. For
clarity, always write parentheses around it if it extends across more
than one line.

Assignment operators and the comma operator (see [Comma
Operator](Comma-Operator.md)) have lower precedence than conditional
expression operators, so write parentheses around those when they appear
inside a conditional expression. See [Order of
Execution](Order-of-Execution.md).
