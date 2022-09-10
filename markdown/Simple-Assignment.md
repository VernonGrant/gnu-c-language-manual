Next: [Lvalues](Lvalues.md), Up: [Assignment
Expressions](Assignment-Expressions.md)  
[Contents](index.md#SEC_Contents "Table of contents")  

------------------------------------------------------------------------


### 7.1 Simple Assignment 


A *simple assignment expression* computes the value of the right operand
and stores it into the lvalue on the left. Here is a simple assignment
expression that stores 5 in `i`:

``` C
i = 5
```

We say that this is an *assignment to* the variable `i` and that it
*assigns* `i` the value 5. It has no semicolon because it is an
expression (so it has a value). Adding a semicolon at the end would make
it a statement (see [Expression Statement](Expression-Statement.md)).

Here is another example of a simple assignment expression. Its operands
are not simple, but the kind of assignment done here is simple
assignment.

``` C
x[foo ()] = y + 6
```

A simple assignment with two different numeric data types converts the
right operand value to the lvalue's type, if possible. It can convert
any numeric type to any other numeric type.

Simple assignment is also allowed on some non-numeric types: pointers
(see [Pointers](Pointers.md)), structures (see [Structure
Assignment](Structure-Assignment.md)), and unions (see
[Unions](Unions.md)).

**Warning:** Assignment is not allowed on arrays because there are no
array values in C; C variables can be arrays, but these arrays cannot be
manipulated as wholes. See [Limitations of C
Arrays](Limitations-of-C-Arrays.md).

See [Assignment Type Conversions](Assignment-Type-Conversions.md), for
the complete rules about data types used in assignments.
