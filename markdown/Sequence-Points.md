Next: [Postincrement and Ordering](Postincrement-and-Ordering.md),
Previous: [Associativity and Ordering](Associativity-and-Ordering.md),
Up: [Order of Execution](Order-of-Execution.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 10.3 Sequence Points 


There are some points in the code where C makes limited guarantees about
the order of operations. These are called *sequence points*. Here is
where they occur:

-   At the end of a *full expression*; that is to say, an expression
    that is not part of a larger expression. All side effects specified
    by that expression are carried out before execution moves on to
    subsequent code.

-   At the end of the first operand of certain operators:
    '`,`', '`&&`', '`||`', and
    '`?:`'. All side effects specified by that expression are
    carried out before any execution of the next operand.

    The commas that separate arguments in a function call are *not*
    comma operators, and they do not create sequence points. The rule
    for function arguments and the rule for operands are different (see
    [Ordering of Operands](Ordering-of-Operands.md)).

-   Just before calling a function. All side effects specified by the
    argument expressions are carried out before calling the function.

    If the function to be called is not constant---that is, if it is
    computed by an expression---all side effects in that expression are
    carried out before calling the function.

The ordering imposed by a sequence point applies locally to a limited
range of code, as stated above in each case. For instance, the ordering
imposed by the comma operator does not apply to code outside the
operands of that comma operator. Thus, in this code,

``` C
(x = 5, foo (x)) + x * x
```

the sequence point of the comma operator orders `x = 5` before
`foo (x)`, but `x * x` could be computed before or after them.

------------------------------------------------------------------------

Next: [Postincrement and Ordering](Postincrement-and-Ordering.md),
Previous: [Associativity and Ordering](Associativity-and-Ordering.md),
Up: [Order of Execution](Order-of-Execution.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
