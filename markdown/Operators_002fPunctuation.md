Next: [Line Continuation](Line-Continuation.md), Previous:
[Identifiers](Identifiers.md), Up: [Lexical
Syntax](Lexical-Syntax.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 5.6 Operators and Punctuation 


Here we describe the lexical syntax of operators and punctuation in C.
The specific operators of C and their meanings are presented in
subsequent chapters.

Most operators in C consist of one or two characters that can't be used
in identifiers. The characters used for operators in C are
'`!~^&|*/%+-=<>,.?:`'.

Some operators are a single character. For instance, '`-`' is
the operator for negation (with one operand) and the operator for
subtraction (with two operands).

Some operators are two characters. For example, '`++`' is the
increment operator. Recognition of multicharacter operators works by
grouping together as many consecutive characters as can constitute one
operator.

For instance, the character sequence '`++`' is always
interpreted as the increment operator; therefore, if we want to write
two consecutive instances of the operator '`+`', we must
separate them with a space so that they do not combine as one token.
Applying the same rule, `a+++++b` is always tokenized as `a++ ++ + b`,
not as `a++ + ++b`, even though the latter could be part of a valid C
program and the former could not (since `a++` is not an lvalue and thus
can't be the operand of `++`).

A few C operators are keywords rather than special characters. They
include `sizeof` (see [Type Size](Type-Size.md)) and `_Alignof` (see
[Type Alignment](Type-Alignment.md)).

The characters '`;{}[]()`' are used for punctuation and
grouping. Semicolon ('`;`') ends a statement. Braces
('`{`' and '`}`') begin and end a block at the
statement level (see [Blocks](Blocks.md)), and surround the
initializer (see [Initializers](Initializers.md)) for a variable with
multiple elements or fields (such as arrays or structures).

Square brackets ('`[`' and '`]`') do array indexing,
as in `array[5]`.

Parentheses are used in expressions for explicit nesting of expressions
(see [Basic Arithmetic](Basic-Arithmetic.md)), around the parameter
declarations in a function declaration or definition, and around the
arguments in a function call, as in `printf ("Foo %d\n", i)` (see
[Function Calls](Function-Calls.md)). Several kinds of statements also
use parentheses as part of their syntax---for instance, `if` statements,
`for` statements, `while` statements, and `switch` statements. See [`if`
Statement](if-Statement.md), and following sections.

Parentheses are also required around the operand of the operator
keywords `sizeof` and `_Alignof` when the operand is a data type rather
than a value. See [Type Size](Type-Size.md).

------------------------------------------------------------------------

Next: [Line Continuation](Line-Continuation.md), Previous:
[Identifiers](Identifiers.md), Up: [Lexical
Syntax](Lexical-Syntax.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
