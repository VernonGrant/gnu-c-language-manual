Next: [Logical Operators and Comparisons](Logicals-and-Comparison.md),
Up: [Execution Control Expressions](Execution-Control-Expressions.md)
 
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 8.1 Logical Operators 


The *logical operators* combine truth values, which are normally
represented in C as numbers. Any expression with a numeric value is a
valid truth value: zero means false, and any other value means true. A
pointer type is also meaningful as a truth value; a null pointer (which
is zero) means false, and a non-null pointer means true (see [Pointer
Types](Pointer-Types.md)). The value of a logical operator is always 1
or 0 and has type `int` (see [Integer Data Types](Integer-Types.md)).

The logical operators are used mainly in the condition of an `if`
statement, or in the end test in a `for` statement or `while` statement
(see [Statements](Statements.md)). However, they are valid in any
context where an integer-valued expression is allowed.

'`! exp`'

-   Unary operator for logical "not." The value is 1 (true) if
    `exp` is 0 (false), and 0 (false) if `exp` is
    nonzero (true).

    **Warning:** if `exp` is anything but an lvalue or a function call,
    you should write parentheses around it.

'`left && right`'

-   The logical "and" binary operator computes `left` and, if
    necessary, `right`. If both of the operands are true, the
    '`&&`' expression gives the value 1 (which is true).
    Otherwise, the '`&&`' expression gives the value 0 (false).
    If `left` yields a false value, that determines the
    overall result, so `right` is not computed.

'`left || right`'

-   The logical "or" binary operator computes `left` and, if
    necessary, `right`. If at least one of the operands is
    true, the '`||`' expression gives the value 1 (which is
    true). Otherwise, the '`||`' expression gives the value 0
    (false). If `left` yields a true value, that determines
    the overall result, so `right` is not computed.

**Warning:** never rely on the relative precedence of '`&&`'
and '`||`'. When you use them together, always use parentheses
to specify explicitly how they nest, as shown here:

``` C
if ((r != 0 && x % r == 0)
    ||
    (s != 0 && x % s == 0))
```

------------------------------------------------------------------------

Next: [Logical Operators and Comparisons](Logicals-and-Comparison.md),
Up: [Execution Control Expressions](Execution-Control-Expressions.md)
 
[Contents](index.md#SEC_Contents "Table of contents")  
