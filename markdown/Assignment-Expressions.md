Next: [Execution Control
Expressions](Execution-Control-Expressions.md), Previous:
[Arithmetic](Arithmetic.md), Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


## 7 Assignment Expressions 


As a general concept in programming, an *assignment* is a construct that
stores a new value into a place where values can be stored---for
instance, in a variable. Such places are called *lvalues* (see
[Lvalues](Lvalues.md)) because they are locations that hold a value.

An assignment in C is an expression because it has a value; we call it
an *assignment expression*. A simple assignment looks like

``` C
lvalue = value-to-store
```

We say it assigns the value of the expression
`value-to-store`{.variable} to the location `lvalue`{.variable}, or that
it stores `value-to-store`{.variable} there. You can think of the "l" in
"lvalue" as standing for "left," since that's what you put on the left
side of the assignment operator.

However, that's not the only way to use an lvalue, and not all lvalues
can be assigned to. To use the lvalue in the left side of an assignment,
it has to be *modifiable*. In C, that means it was not declared with the
type qualifier `const` (see [`const` Variables and Fields](const.md)).

The value of the assignment expression is that of `lvalue`{.variable}
after the new value is stored in it. This means you can use an
assignment inside other expressions. Assignment operators are
right-associative so that

``` C
x = y = z = 0;
```

is equivalent to

``` C
x = (y = (z = 0));
```

This is the only useful way for them to associate; the other way,

``` C
((x = y) = z) = 0;
```

would be invalid since an assignment expression such as `x = y` is not
valid as an lvalue.

**Warning:** Write parentheses around an assignment if you nest it
inside another expression, unless that is a conditional expression, or
comma-separated series, or another assignment.

-   [Simple Assignment](Simple-Assignment.md)
-   [Lvalues](Lvalues.md)
-   [Modifying Assignment](Modifying-Assignment.md)
-   [Increment and Decrement Operators](Increment_002fDecrement.md)
-   [Postincrement and
    Postdecrement](Postincrement_002fPostdecrement.md)
-   [Pitfall: Assignment in
    Subexpressions](Assignment-in-Subexpressions.md)
-   [Write Assignments in Separate
    Statements](Write-Assignments-Separately.md)

------------------------------------------------------------------------

Next: [Execution Control
Expressions](Execution-Control-Expressions.md), Previous:
[Arithmetic](Arithmetic.md), Up: [GNU C Manual](index.md)  
[Contents](index.md#SEC_Contents "Table of contents")  
