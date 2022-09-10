Previous: [Labels as Values](Labels-as-Values.md), Up:
[Statements](Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 19.15 Statements and Declarations in Expressions 


A block enclosed in parentheses can be used as an expression in GNU C.
This provides a way to use local variables, loops and switches within an
expression. We call it a *statement expression*.

Recall that a block is a sequence of statements surrounded by braces. In
this construct, parentheses go around the braces. For example:

``` C
({ int y = foo (); int z;
   if (y > 0) z = y;
   else z = - y;
   z; })
```

is a valid (though slightly more complex than necessary) expression for
the absolute value of `foo ()`.

The last statement in the block should be an expression statement; an
expression followed by a semicolon, that is. The value of this
expression serves as the value of statement expression. If the last
statement is anything else, the statement expression's value is `void`.

This feature is mainly useful in making macro definitions compute each
operand exactly once. See [Using `__auto_type` for Local
Variables](Macros-and-Auto-Type.md).

Statement expressions are not allowed in expressions that must be
constant, such as the value for an enumerator, the width of a bit-field,
or the initial value of a static variable.

Jumping into a statement expression---with `goto`, or using a `switch`
statement outside the statement expression---is an error. With a
computed `goto` (see [Labels as Values](Labels-as-Values.md)), the
compiler can't detect the error, but it still won't work.

Jumping out of a statement expression is permitted, but since
subexpressions in C are not computed in a strict order, it is
unpredictable which other subexpressions will have been computed by
then. For example,

``` C
  foo (), (({ bar1 (); goto a; 0; }) + bar2 ()), baz();
```

calls `foo` and `bar1` before it jumps, and never calls `baz`, but may
or may not call `bar2`. If `bar2` does get called, that occurs after
`foo` and before `bar1`.

------------------------------------------------------------------------

Previous: [Labels as Values](Labels-as-Values.md), Up:
[Statements](Statements.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
